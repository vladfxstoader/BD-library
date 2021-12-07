--Exercitiul 11.

--1. Sa se afiseze angajatii bibliotecilor care se afla in Pitesti, precum si
--salariul acestora, stiind ca li se acorda o majorare de salariu de 15%.

--Am folosit NVL, filtrare la nivel de linii si subcereri nesincronizate

select nume, prenume, functie, NVL(salariu+0.15*salariu,0) "SALARIU DUPA MAJORARE"
from angajat
where id_biblioteca in (select id_biblioteca from biblioteca where id_locatie=
                        (select id_locatie from locatie where upper(nume)='PITESTI'));



--2. Sa se afiseze cititorii care au imprumutat carti din domeniile Literatura romana,
--Fictiune sau carti scrise de Murakami si care au imprumutat carti intr-o zi 
--de miercuri si le-au adus la timp, ordonati alfabetic dupa nume.

--am folosit join pe 4 tabele, filtrare la nivel de linii, subcereri nesincronizate
--pe 3 tabele, ordonari, functii pe siruri de caractere si pe date calendaristice.

select distinct(c.id_cititor),c.prenume,c.nume
from cititor c, istoric i, domeniu d, carte c1
where c.id_cititor=i.id_cititor and i.data_limita>=i.data_restituire and
i.id_carte=c1.id_carte and to_char(i.data_imprumutului,'DAY') in ('WEDNESDAY')
and c1.id_carte in (select id_carte from apartine where id_domeniu in 
(select id_domeniu from domeniu where upper(nume)='LITERATURA ROMANA' or upper(nume)='FICTIUNE')
or c1.id_carte in (select id_carte from scriere where id_autor=(select id_autor
from autor where upper(nume)='MURAKAMI')))
order by c.prenume;



--3. Sa se afiseze numele, functia angajatilor, biblioteca unde lucreaza si salariul 
--acestora stiind ca se majoreaza salariile astfel: pentru manageri cu 20%, pentru 
-- bibliotecari cu 15%, pentru paznici cu 10% si pentru ingrijitori cu 5%. Afisati
--doar angajatii care s-au angajat dupa anul 2015, in ordinea lexicografica a functiilor.
                        
--Am folosit decode, ordonare si functie pentru a prelucra date calendaristice.
                        
select a.nume,a.prenume,a.functie,b.nume "Biblioteca",
decode (upper(a.functie), 'MANAGER', NVL(salariu+0.2*salariu,0),
                          'BIBLIOTECAR', NVL(salariu+0.15*salariu,0),
                          'PAZNIC', NVL(salariu+0.1*salariu,0),
                          'INGRIJITOR', NVL(salariu+0.05*salariu,0)) "Salariu majorat"
from angajat a, biblioteca b
where b.id_biblioteca=a.id_biblioteca and a.data_angajarii>=
                                        to_date('01/01/2015','dd/mm/yyyy')
order by a.functie;   



--4. Sa se afiseze numele si pretul cartilor care sunt scrise de cel putin 2 autori.
--Incadrati cartile in categorii dupa numarul de pagini, astfel: daca au sub 350 de pagini,
--sunt considerate lectura usoara, daca au intre 350 si 400 de pagini, sunt considerate
--lectura cu dificultate medie, iar daca au peste 400 de pagini sunt considerate lecturi 
--grele.

--Am folosit grupari de date, functii grup, filtrare la nivel de grupuri si functia case

select c.nume, c.pret, g.nr "NR AUTORI", 
case
    when c.numar_pagini<350 then 'dificultate usoara'
    when c.numar_pagini>=350 and c.numar_pagini<400 then 'dificultate medie'
    when c.numar_pagini>=400 then 'dificultate grea'
end as "TIP DE LECTURA"
from carte c,(select count(*) nr, id_carte idc
from scriere
group by id_carte
having count(*)>1) g
where c.id_carte=g.idc;



--5. Sa se afiseze pentru fiecare angajat care are salariul mai mare decat media
--salariului tuturor angajatilor numele, prenumele, salariu, functia, salariul
--mediu per functie, numarul de angajati per functie si biblioteca unde lucreaza.

--Am folosit subcereri sincronizate, filtrare la nivel de linii si clauza with

WITH tabtemp as(
select avg(salariu) as medie
from angajat)

select nume,prenume,salariu,e.functie,
(select round(avg(salariu))
from angajat
where functie=e.functie) "SALARIU MEDIU/FUNCTIE",
(select count(*)
from angajat
where functie=e.functie) "NR ANGAJATI/FUNCTIE",
(select nume
from biblioteca
where id_biblioteca=e.id_biblioteca) "BIBLIOTECA"
from angajat e, tabtemp t
where e.salariu>t.medie
order by e.functie



--Exercitiul 12.

--Sa se mareasca salariul angajatilor care lucreaza la biblioteci aflate in Pitesti
--cu 20%.

update angajat
set salariu = salariu+0.2*salariu
where id_biblioteca in (select id_biblioteca from biblioteca 
where id_locatie = (select id_locatie from locatie where upper(nume) = 'PITESTI'));

--Sa se reduca pretul cartilor publicate la editura RAO cu 50%.

update carte
set pret=pret-0.5*pret
where id_carte in (select id_carte from carte 
where id_editura = (select id_editura from editura where upper(nume)='RAO'));

--Sa se stearga locatiile in care nu se afla nicio biblioteca.

delete from locatie
where id_locatie not in (select id_locatie from biblioteca);


--Exercitiul 13. 

--Secventele se gasesc in "creare-inserare.txt", la tabelele AUTOR, 
--CITITOR, CARTE, APARTINE, ANGAJAT, ABONAMENT, IMPRUMUT, ISTORIC.



--Exercitiul 16.

--OUTER JOIN
--Afisati pentru fiecare cititor cartea imprumutata si editura acesteia.

select c.nume||' '||c.prenume CITITOR, c1.nume CARTE, e.nume EDITURA
from cititor c right outer join istoric i on (i.id_cititor = c.id_cititor)
left outer join carte c1 on (c1.id_carte = i.id_carte) full outer join editura
e on (e.id_editura = c1.id_editura)
order by c.nume; 



-DIVISION
--Sa se afiseze id-ul, numele si prenumele cititorilor care au imprumutat 
--doar carti cu pretul sub 15 lei.

select i.id_cititor, nume, prenume
from istoric i join cititor c on (i.id_cititor=c.id_cititor)
where id_carte in (select id_carte from carte where pret<=15)
group by i.id_cititor,nume, prenume
having count(*) <= (select count(id_carte) from carte where pret<=15)

minus

select i.id_cititor, nume, prenume
from istoric i join cititor c on (i.id_cititor=c.id_cititor)
where id_carte not in (select id_carte from carte where pret<=15)



--Sa se afiseze cititorii care au imprumutat aceleasi carti ca cititorul cu id-ul 20.

select i.id_cititor, nume, prenume
from istoric i join cititor c on (c.id_cititor = i.id_cititor)
where id_carte in (select id_carte
                    from istoric
                    where id_cititor=20)
and i.id_cititor !=20
minus

select i.id_cititor, nume, prenume
from istoric i join cititor c on (c.id_cititor = i.id_cititor)
where id_carte not in (select id_carte
                    from istoric
                    where id_cititor=20);
