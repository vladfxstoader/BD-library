--CREARE SI INSERARE IN TABELA AUTOR

--A se verifica ca prima valoare a secventei sa fie 1, pentru a garanta corectitudinea datelor.

CREATE TABLE autor
(id_autor number(5) constraint pk_autor primary key,
nume varchar2(20),
prenume varchar2(20),
data_nasterii date
);

CREATE SEQUENCE SEQ_AUTOR
INCREMENT by 1
START WITH 1
MAXVALUE 1000
NOCYCLE;

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Creanga', 'Ion', to_date('01/03/1837','dd/mm/yyyy'));

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Eminescu', 'Mihai', to_date('15/01/1850','dd/mm/yyyy'));

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Eliade', 'Mircea', to_date('13/03/1907','dd/mm/yyyy'));

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Sadoveanu', 'Mihail', to_date('05/11/1880','dd/mm/yyyy'));

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Serghi', 'Cella', to_date('04/11/1907','dd/mm/yyyy'));

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Petrescu', 'Camil', to_date('22/04/1894','dd/mm/yyyy'));

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Slavici', 'Ioan', to_date('18/01/1848','dd/mm/yyyy'));

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Rowling', 'Joanne', to_date('31/07/1965','dd/mm/yyyy'));

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Silvera', 'Adam', to_date('07/06/1990','dd/mm/yyyy'));

INSERT INTO autor
VALUES (SEQ_AUTOR.NEXTVAL, 'Murakami', 'Haruki', to_date('12/01/1949','dd/mm/yyyy'));

COMMIT;



--CREARE SI INSERARE IN TABELA EDITURA

CREATE TABLE editura
(id_editura number(5) constraint pk_editura primary key,
nume varchar2(20),
telefon varchar2(15)
);

INSERT INTO editura
VALUES (1, 'Litera', '0374826635');

INSERT INTO editura
VALUES (2,'Humanitas', '0214088350');

INSERT INTO editura
VALUES (3, 'Polirom', '0232217440'); 

INSERT INTO editura
VALUES (4, 'Corint', '0213194820');

INSERT INTO editura
VALUES (5, 'RAO', '0729166965');

COMMIT;



--CREARE SI INSERARE IN TABELA DOMENIU

CREATE TABLE domeniu
(id_domeniu number(5) constraint pk_domeniu primary key,
nume varchar2(20)
);

INSERT INTO domeniu
VALUES(1,'Fictiune');

INSERT INTO domeniu
VALUES(2,'Literatura clasica');

INSERT INTO domeniu
VALUES(3,'Young adult');

INSERT INTO domeniu
VALUES(4,'Science fiction');

INSERT INTO domeniu
VALUES(5,'Aventura');

INSERT INTO domeniu
VALUES(6,'Literatura romana');

COMMIT;



--CREARE SI INSERARE IN TABELA LOCATIE

CREATE TABLE locatie
(id_locatie number(5) constraint pk_locatie primary key,
nume varchar2(20)
);

INSERT INTO locatie
VALUES(1,'Bucuresti');

INSERT INTO locatie
VALUES(2,'Iasi');

INSERT INTO locatie
VALUES(3,'Pitesti');

INSERT INTO locatie
VALUES(4,'Timisoara');

INSERT INTO locatie
VALUES(5,'Cluj-Napoca');

INSERT INTO locatie
VALUES (6, 'Slatina');

INSERT INTO locatie
values (7, 'Piatra Neamt');

COMMIT;



--CREARE SI INSERARE IN TABELA CITITOR

CREATE TABLE cititor
(id_cititor number(5) constraint pk_cititor primary key,
nume varchar2(20),
prenume varchar2(20),
telefon varchar2(15)
);

CREATE SEQUENCE SEQ_CITITOR
INCREMENT by 1
START WITH 1
MAXVALUE 1000
NOCYCLE;

INSERT INTO cititor
VALUES(SEQ_CITITOR.NEXTVAL,'Toader','Vlad','0751968771');

INSERT INTO cititor
VALUES(SEQ_CITITOR.NEXTVAL,'Popescu','Ilinca','0775200135');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Fierbinteanu','David','0762111320');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Florea','Alexandra','0734231224');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Ilinca','Flavius','0745874914');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Sandu','Maria','0756204355');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Morar','Ramona','0721234222');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Maria','Viorica','0786235333');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL, 'Ilie','Ovidiu','0763223453');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Toma','Carmen','0792331234');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Nicolae','Florina','0745375312');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Marin','Dorin','0742543212');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Grigore','Denisa','0756320488');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Bratu','Sonia','0785698210');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL, 'Toderoiu','Gabriel','0794212333');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL, 'Boboc','Georgiana','0764122353');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Vladau','Adrian','0764122331');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Bican','Serban','0754231567');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL,'Alexe','Stefana','0752122353');

INSERT INTO cititor
VALUES (SEQ_CITITOR.NEXTVAL, 'Szabo', 'Richard', '0753211354');

COMMIT;



--CREARE SI INSERARE IN TABELA CARTE

CREATE TABLE carte
(id_carte number(5) constraint pk_carte primary key,
nume varchar2(20),
numar_pagini number(4),
pret number(3),
id_editura number(5), 
constraint fk_carte foreign key (id_editura) references EDITURA(id_editura)
);

CREATE SEQUENCE SEQ_CARTE
INCREMENT by 1
START WITH 1
MAXVALUE 1000
NOCYCLE;

ALTER TABLE carte MODIFY nume varchar2(40);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Amintiri din copilarie',269, 9.5, 1);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Poezii',256, 8, 2);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL, 'Maitreyi',200,18,3);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL, 'La tiganci',188, 17.34,3);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL, 'Romanul adolescentului miop', 368, 35, 4);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL, 'Nunta in cer', 160,22,2);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Dumbrava minunata',48,15,1);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Baltagul',210,22,4);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Hanu Ancutei',152,19.5,5);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Cartea Mironei',496,19.9,4);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Panza de paianjen',480,36.6,3);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Patul lui Procust',336,27,1);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Jocul Ielelor',320,32,2);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Mara',319,12,4);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Moara cu noroc',192,13,3);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Harry Potter si piatra filosofala',256,69,4);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Harry Potter si prizonierul din Azkaban',462,49,4);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Harry Potter si Talismanele Mortii',784,65,4);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Padurea norvegiana',360,27,3);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'1Q84',448,28,3);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Trecutul e tot ce mi-ai lasat',376,33,5);

INSERT INTO carte
VALUES (SEQ_CARTE.NEXTVAL,'Amandoi mor la sfarsit',336,45,5);

COMMIT;



--CREARE SI INSERARE IN TABELA BIBLIOTECA

CREATE TABLE biblioteca
(id_biblioteca number(5) constraint pk_biblioteca primary key,
nume varchar2(20),
adresa varchar2(40),
tip_biblioteca varchar2(20),
id_locatie number(5), 
constraint fk_biblioteca foreign key (id_locatie) references LOCATIE(id_locatie),
constraint check_tip_biblioteca check(upper(tip_biblioteca) in ('MUNINCIPALA','SCOLARA'))
);


INSERT INTO biblioteca
VALUES(1,'Mihai Eminescu','Bd. Unirii, nr. 5, sector 1','Munincipala',1);

INSERT INTO biblioteca
VALUES (2,'Dinicu Golescu', 'Piata Juramantului, nr. 12','Munincipala',3);

INSERT INTO biblioteca
VALUES (3,'Tudor Musatescu','Strada Negru Voda, nr. 66','Scolara',2);

INSERT INTO biblioteca
VALUES (4,'Munincipala nr.5','Bd. Eroilor, nr. 336, corp A','Munincipala',4);

INSERT INTO biblioteca
VALUES (5,'Dan Barbilian','Strada Dezrobirii, nr. 37','Scolara',5);

COMMIT;



--CREARE SI INSERARE IN TABELA APARTINE

CREATE TABLE apartine
(id_apartinere number(5) constraint pk_apartinere primary key,
id_carte number(5),
id_domeniu number(5),
constraint fk_apartine_domeniu foreign key (id_domeniu) references DOMENIU(id_domeniu),
constraint fk_apartine_carte foreign key (id_carte) references CARTE(id_carte)
);

CREATE SEQUENCE SEQ_APARTINE
INCREMENT by 1
START WITH 1
MAXVALUE 1000
NOCYCLE;

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,3,2);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,3,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,3,5);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,4,2);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,4,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,5,2);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,5,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,5,5);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,6,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,7,2);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,7,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,8,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,9,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,8,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,9,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,10,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,10,2);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,10,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,10,5);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,11,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,11,2);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,12,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,12,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,13,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,14,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,14,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,15,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,16,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,16,2);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,16,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,17,2);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,17,6);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,18,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,18,3);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,18,5);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,19,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,19,3);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,19,5);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,20,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,20,3);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,20,5);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,21,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,22,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,23,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,23,3);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,24,1);

INSERT INTO apartine
VALUES(SEQ_APARTINE.NEXTVAL,24,3);

COMMIT;



--CREARE SI INSERARE IN TABELA SCRIERE

CREATE TABLE scriere
(id_scriere number(5) constraint pk_scriere primary key,
id_autor number(5),
id_carte number(5),
constraint fk_scriere_autor foreign key (id_autor) references AUTOR(id_autor),
constraint fk_scriere_carte foreign key (id_carte) references CARTE(id_carte)
);

INSERT INTO scriere
VALUES (1,1,3);

INSERT INTO scriere
VALUES (2,2,4);

INSERT INTO scriere
VALUES (3,3,5);

INSERT INTO scriere
VALUES (4,3,6);

INSERT INTO scriere
VALUES (5,3,7);

INSERT INTO scriere
VALUES (6,3,8);

INSERT INTO scriere
VALUES (7,4,9);

INSERT INTO scriere
VALUES (8,4,10);

INSERT INTO scriere
VALUES (9,4,11);

INSERT INTO scriere
VALUES (10,5,12);

INSERT INTO scriere
VALUES (11,5,13);

INSERT INTO scriere
VALUES (12,6,13);

INSERT INTO scriere
VALUES (13,6,14);

INSERT INTO scriere
VALUES (14,6,15);

INSERT INTO scriere
VALUES (15,3,15);

INSERT INTO scriere
VALUES (16,7,16);

INSERT INTO scriere
VALUES (17,7,17);

INSERT INTO scriere
VALUES (18,8,18);

INSERT INTO scriere
VALUES (26,8,19);

INSERT INTO scriere
VALUES (19,8,20);

INSERT INTO scriere
VALUES (20,10,21);

INSERT INTO scriere
VALUES (21,10,22);

INSERT INTO scriere
VALUES (22,9,23);

INSERT INTO scriere
VALUES (23,9,24);

INSERT INTO scriere
VALUES (24,8,23);

INSERT INTO scriere
VALUES (25,10,23);

COMMIT;



--CREARE SI INSERARE IN TABELA ANGAJAT

CREATE TABLE angajat
(id_angajat number(5) constraint pk_angajat primary key,
nume varchar2(20),
prenume varchar2(20),
salariu number(5),
functie varchar2(20),
data_angajarii date,
id_biblioteca number(5),
constraint fk_angajat foreign key (id_biblioteca) references BIBLIOTECA(id_biblioteca),
constraint check_functie_angajat check (upper(functie) in ('MANAGER','BIBLIOTECAR','PAZNIC','INGRIJITOR'))
);

CREATE SEQUENCE SEQ_ANGAJAT
INCREMENT by 1
START WITH 1
MAXVALUE 1000
NOCYCLE;

INSERT INTO angajat
VALUES(SEQ_ANGAJAT.NEXTVAL,'Antonescu','Ovidiu',3500,'Manager',to_date('30/06/2015','dd/mm/yyyy'),2);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Cordun','Diana',2900,'Bibliotecar',to_date('12/11/2017','dd/mm/yyyy'),2);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Scheianu','Anisia',2800,'Bibliotecar',to_date('08/05/2019','dd/mm/yyyy'),2);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Avram','Catalin',2300,'Paznic',to_date('23/01/2020','dd/mm/yyyy'),2);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Catana','Ionela',2000,'Ingrijitor',to_date('15/08/2014','dd/mm/yyyy'),2);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Cuza','Catalina',3600,'Manager',to_date('11/11/2011','dd/mm/yyyy'),3);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Satarbasa','Carmen',3000,'Bibliotecar',to_date('01/06/2012','dd/mm/yyyy'),3);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Parghel','Petre',3700,'Manager',to_date('01/09/2008','dd/mm/yyyy'),4);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Negus','Laura',3500,'Bibliotecar',to_date('14/05/2011','dd/mm/yyyy'),4);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Oproiu','Laurentiu',3600,'Bibliotecar',to_date('26/02/2012','dd/mm/yyyy'),4);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Dorcioman','Dana',3000,'Paznic',to_date('23/06/2007','dd/mm/yyyy'),4);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Bratu','Ionut',2400,'Bibliotecar',to_date('24/05/2015','dd/mm/yyyy'),5);

INSERT INTO angajat
VALUES (SEQ_ANGAJAT.NEXTVAL,'Broscoteanu','David',3250,'Bibliotecar',to_date('11/04/2021','dd/mm/yyyy'),2);

COMMIT;



--CREARE SI INSERARE IN TABELA ABONAMENT

CREATE TABLE abonament
(id_abonament number(5) constraint pk_abonament primary key,
pret number(4),
data_expirarii date,
id_cititor number(5),
constraint fk_abonament foreign key(id_cititor) references CITITOR(id_cititor)
);

CREATE SEQUENCE SEQ_ABONAMENT
INCREMENT by 1
START WITH 1
MAXVALUE 1000
NOCYCLE;

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,20,to_date('30/06/2021','dd/mm/yyyy'),2);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,25,to_date('01/01/2022','dd/mm/yyyy'),3);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,20,to_date('04/02/2021','dd/mm/yyyy'),4);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,22.5,to_date('13/06/2021','dd/mm/yyyy'),5);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,24,to_date('30/07/2021','dd/mm/yyyy'),7);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,25,to_date('01/03/2022','dd/mm/yyyy'),2);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,30,to_date('30/06/2022','dd/mm/yyyy'),8);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,15,to_date('12/02/2021','dd/mm/yyyy'),9);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,17.5,to_date('22/03/2021','dd/mm/yyyy'),11);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,23,to_date('17/09/2021','dd/mm/yyyy'),12);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,14,to_date('01/01/2021','dd/mm/yyyy'),14);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,20,to_date('19/10/2021','dd/mm/yyyy'),14);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,18,to_date('28/04/2021','dd/mm/yyyy'),15);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,35,to_date('31/12/2022','dd/mm/yyyy'),16);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,22.5,to_date('22/06/2021','dd/mm/yyyy'),18);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,25,to_date('31/07/2021','dd/mm/yyyy'),19);

INSERT INTO abonament
VALUES (SEQ_ABONAMENT.NEXTVAL,31.5,to_date('22/04/2022','dd/mm/yyyy'),20);

COMMIT;



--CREARE SI INSERARE IN TABELA IMPRUMUT

CREATE TABLE imprumut
(id_imprumut number(5) constraint pk_imprumut primary key,
id_cititor number(5),
id_carte number(5),
id_biblioteca number(5),
constraint fk_imprumut_cititor foreign key(id_cititor) references CITITOR(id_cititor),
constraint fk_imprumut_carte foreign key(id_carte) references CARTE(id_carte),
constraint fk_imprumut_biblioteca foreign key(id_biblioteca) references BIBLIOTECA(id_biblioteca)
);

CREATE SEQUENCE SEQ_IMPRUMUT
INCREMENT BY 1
START WITH 1
MAXVALUE 1000
NOCYCLE;

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,2,23,2);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,3,4,3);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,4,15,2);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,5,8,1);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,6,12,4);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,7,7,2);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,8,15,5);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,9,3,2);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,10,7,5);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,11,9,4);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,12,19,3);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,13,22,1);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,14,24,2);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,15,16,3);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,16,9,4);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,17,3,2);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,18,4,4);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,19,13,5);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,20,3,1);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,21,18,3);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,3,6,3);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,4,8,2);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,2,22,2);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,7,15,5);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,13,5,3);

INSERT INTO imprumut
VALUES (SEQ_IMPRUMUT.NEXTVAL,18,3,5);

COMMIT;



--CREARE SI INSERARE IN TABELA ISTORIC

CREATE TABLE istoric
(id_istoric number(5) constraint pk_istoric primary key,
id_carte number(5),
id_cititor number(5),
data_imprumutului date,
data_limita date,
data_restituire date,
constraint fk_istoric_carte foreign key(id_carte) references CARTE(id_carte),
constraint fk_istoric_cititor foreign key(id_cititor) references CITITOR(id_cititor),
constraint check_data check(data_limita>data_imprumutului)
);

CREATE SEQUENCE SEQ_ISTORIC
INCREMENT by 1
START WITH 1
MAXVALUE 1000
NOCYCLE;

INSERT INTO istoric
VALUES(SEQ_ISTORIC.NEXTVAL,23,2,to_date('23/01/2021','dd/mm/yyyy'),to_date('31/01/2021','dd/mm/yyyy'),to_date('30/01/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,4,3,to_date('13/03/2021','dd/mm/yyyy'),to_date('27/03/2021','dd/mm/yyyy'),to_date('27/03/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,15,4,to_date('27/12/2020','dd/mm/yyyy'),to_date('11/01/2021','dd/mm/yyyy'),to_date('09/01/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,8,5,to_date('06/02/2021','dd/mm/yyyy'),to_date('20/02/2021','dd/mm/yyyy'),to_date('26/02/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,12,6,to_date('11/04/2021','dd/mm/yyyy'),to_date('25/04/2021','dd/mm/yyyy'),to_date('21/04/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,15,8,to_date('13/06/2021','dd/mm/yyyy'),to_date('27/06/2021','dd/mm/yyyy'),to_date('14/06/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,3,9,to_date('09/12/2020','dd/mm/yyyy'),to_date('23/12/2020','dd/mm/yyyy'),to_date('20/12/2020','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,7,10,to_date('01/03/2021','dd/mm/yyyy'),to_date('15/03/2021','dd/mm/yyyy'),to_date('06/04/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,9,11,to_date('18/04/2021','dd/mm/yyyy'),to_date('25/04/2021','dd/mm/yyyy'),to_date('23/04/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,19,12,to_date('28/01/2021','dd/mm/yyyy'),to_date('07/02/2021','dd/mm/yyyy'),to_date('07/02/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,22,13,to_date('09/03/2021','dd/mm/yyyy'),to_date('16/03/2021','dd/mm/yyyy'),to_date('17/03/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,24,14,to_date('17/02/2021','dd/mm/yyyy'),to_date('24/02/2021','dd/mm/yyyy'),to_date('23/02/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,16,15,to_date('18/03/2021','dd/mm/yyyy'),to_date('01/04/2021','dd/mm/yyyy'),to_date('03/04/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES(SEQ_ISTORIC.NEXTVAL,9,16,to_date('01/11/2020','dd/mm/yyyy'),to_date('15/11/2020','dd/mm/yyyy'),to_date('16/11/2020','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,3,17,to_date('19/05/2021','dd/mm/yyyy'),to_date('13/06/2021','dd/mm/yyyy'),to_date('06/06/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,4,18,to_date('30/05/2021','dd/mm/yyyy'),to_date('15/06/2021','dd/mm/yyyy'),NULL);

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,13,19,to_date('06/06/2021','dd/mm/yyyy'),to_date('30/06/2021','dd/mm/yyyy'),NULL);

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,3,20,to_date('25/02/2021','dd/mm/yyyy'),to_date('05/03/2021','dd/mm/yyyy'),to_date('04/03/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,18,21,to_date('18/01/2021','dd/mm/yyyy'),to_date('01/02/2021','dd/mm/yyyy'),NULL);

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,6,3,to_date('19/03/2021','dd/mm/yyyy'),to_date('03/04/2021','dd/mm/yyyy'),to_date('24/03/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,8,4,to_date('01/03/2021','dd/mm/yyyy'),to_date('01/04/2021','dd/mm/yyyy'),to_date('27/03/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,22,2,to_date('19/05/2021','dd/mm/yyyy'),to_date('03/06/2021','dd/mm/yyyy'),to_date('20/05/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,15,7,to_date('04/02/2021','dd/mm/yyyy'),to_date('18/02/2021','dd/mm/yyyy'),to_date('27/02/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,5,13,to_date('15/01/2021','dd/mm/yyyy'),to_date('29/01/2021','dd/mm/yyyy'),to_date('31/01/2021','dd/mm/yyyy'));

INSERT INTO istoric
VALUES (SEQ_ISTORIC.NEXTVAL,3,18,to_date('07/03/2021','dd/mm/yyyy'),to_date('03/04/2021','dd/mm/yyyy'),to_date('19/03/2021','dd/mm/yyyy'));

COMMIT;



--ADAUGAREA CONSTRANGERILOR NOT NULL TABELELOR

ALTER TABLE editura MODIFY nume not null;
ALTER TABLE domeniu MODIFY nume not null;
ALTER TABLE autor MODIFY nume not null;
ALTER TABLE autor MODIFY prenume not null;
ALTER TABLE carte MODIFY nume not null;
ALTER TABLE carte MODIFY id_editura not null;
ALTER TABLE abonament MODIFY id_cititor not null;
ALTER TABLE cititor MODIFY nume not null;
ALTER TABLE cititor MODIFY prenume not null;
ALTER TABLE angajat MODIFY nume not null;
ALTER TABLE angajat MODIFY prenume not null;
ALTER TABLE angajat MODIFY id_biblioteca not null;
ALTER TABLE locatie MODIFY nume not null;
ALTER TABLE biblioteca MODIFY nume not null;
ALTER TABLE biblioteca MODIFY tip_biblioteca not null;
ALTER TABLE biblioteca MODIFY id_locatie not null;
ALTER TABLE istoric MODIFY id_cititor not null;
ALTER TABLE istoric MODIFY id_carte not null;
ALTER TABLE scriere MODIFY id_autor not null;
ALTER TABLE scriere MODIFY id_carte not null;

COMMIT;

