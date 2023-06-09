create table Joburi(
id_job number(4) primary key,
nume_job varchar2(10) not null
);

create table ComicStore(
id_comic_store number(4) primary key,
nume_store varchar2(15) not null
);

create table Top(
id_top number(4) primary key,
denumire_top varchar2(20) not null
);

create table Cumparator(
id_cumparator number(4) primary key,
nume varchar2(12) not null,
prenume varchar2(12) not null,
varsta number(4) not null
);

create table Review(
id_review number(4) primary key,
descriere_review varchar2(30) not null
);

create table ComicBook(
id_comic_book number(4) primary key,
id_comic_store number(4) references ComicStore(id_comic_store) on delete cascade,
id_top number(4) references Top(id_top) on delete cascade,
id_cumparator number(4) references Cumparator(id_cumparator) on delete cascade,
nume varchar2(20) not null,
pret number(4) not null
);

create table Angajat(
id_angajat number(4) primary key,
id_job number(4) references Joburi(id_job) on delete cascade,
id_comic_store number(4) references ComicStore(id_comic_store) on delete cascade,
nume varchar2(10) not null,
prenume varchar2(10) not null,
telefon number(11) not null unique
);

create table Vinde(
id_angajat number(4),
id_comic_book number(4),
primary key(id_angajat, id_comic_book),
foreign key(id_angajat) references Angajat(id_angajat) on delete cascade,
foreign key(id_comic_book) references ComicBook(id_comic_book) on delete cascade
);

create table Primeste(
id_review number(4),
id_comic_book number(4),
primary key(id_review, id_comic_book),
foreign key(id_review) references Review(id_review) on delete cascade,
foreign key(id_comic_book) references ComicBook(id_comic_book) on delete cascade
);

create table Ofera(
id_review number(4),
id_cumparator number(4),
primary key(id_review, id_cumparator),
foreign key(id_review) references Review(id_review) on delete cascade,
foreign key(id_cumparator) references Cumparator(id_cumparator) on delete cascade
);

--drop table Joburi;
--drop table ComicStore;
--drop table Top;
--drop table Cumparator;
--drop table Review;
--drop table ComicBook;
--drop table Angajat;
--drop table Vinde;
--drop table Primeste;
--drop table Ofera;

-----secvente-----
create sequence angajati
start with 1
nocycle;

create sequence jobs
start with 1
nocycle;

create sequence comics
start with 1
nocycle;

create sequence comic_store
start with 1
nocycle;

create sequence tops
start with 1
nocycle;

create sequence cumparatori
start with 1
nocycle;

create sequence reviews
start with 1 
nocycle;

insert into Joburi(id_job, nume_job)
values(jobs.nextval, 'Vanzator');

insert into Joburi(id_job, nume_job)
values(jobs.nextval, 'Manager');

insert into Joburi(id_job, nume_job)
values(jobs.nextval, 'Asistent');

insert into Joburi(id_job, nume_job)
values(jobs.nextval, 'Patron');

insert into Joburi(id_job, nume_job)
values(jobs.nextval, 'Curatator');

insert into Joburi(id_job, nume_job)
values(jobs.nextval, 'Investitor');

insert into Joburi(id_job, nume_job)
values(jobs.nextval, 'Asistent');

----
insert into ComicStore(id_comic_store, nume_store)
values (comic_store.nextval, 'Best Books');

insert into ComicStore(id_comic_store, nume_store)
values (comic_store.nextval, 'Hentai Heaven');

insert into ComicStore(id_comic_store, nume_store)
values (comic_store.nextval, 'Top Comics');

insert into ComicStore(id_comic_store, nume_store)
values (comic_store.nextval, 'Last Avengers');

insert into ComicStore(id_comic_store, nume_store)
values (comic_store.nextval, 'Downtown Comics');

insert into ComicStore(id_comic_store, nume_store)
values (comic_store.nextval, 'New Order Shop');

insert into ComicStore(id_comic_store, nume_store)
values (comic_store.nextval, 'Stranger Shop');

insert into ComicStore(id_comic_store, nume_store)
values (comic_store.nextval, 'Big Offer');

insert into ComicStore(id_comic_store, nume_store)
values (comic_store.nextval, 'New Nw');

--drop sequence angajati;
--drop sequence jobs;
--drop sequence comics;
--drop sequence comic_store;
--drop sequence tops;
--drop sequence cumparatori;
--drop sequence reviews;


insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,1,1, 'Ciocan', 'Madalin', 40763312934);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,2,1, 'Silviu', 'Lungu', 40763312314);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,3,1, 'Matea', 'Marian', 40762345674);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,4,2, 'Liviu', 'Sandu', 40743212934);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,5,2, 'Spataru', 'Sulean', 40743444934);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,1,2, 'Coltea', 'Spitalu', 40733312934);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,3,2, 'Cosmina', 'Ciortea', 40743299934);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,2,2, 'Sandu', 'Ciorba', 40712312734);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,5,1, 'Florin', 'Florin', 40743123454);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,4,1, 'Florin', 'Dinu', 40746754454);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,2,3, 'Martinel', 'Lungu', 40743555554);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,1,3, 'Guta', 'Nicolae', 40711123454);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,4,3, 'Trinu', 'Minu', 40743187874);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,5,4, 'Legion', 'Seven', 40741212654);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,2,4, 'Cultan', 'Oirr', 40755123552);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,1,4, 'Petrica', 'Simion', 40743666884);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,5,4, 'Minuc', 'Sad', 40724561834);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,1,5, 'Sidan', 'Pisan', 40215384912);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,2,5, 'Lionel', 'Messi', 40724444434);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,1,5, 'Cristiano', 'Ronaldo', 40724656224);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,5,5, 'Vecinu', 'Debloc', 40712361994);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,2,6, 'Ghioc', 'David', 40721122334);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,1,6, 'Flesa', 'Manar', 40754222811);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,3,6, 'Tarnaveanu', 'Sorin', 40724141794);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,4,6, 'Scovearca', 'Ramus', 40214563151);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,4,6, 'Sive', 'Relu', 40214999951);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,2,7, 'Svde', 'Rreu', 40223561711);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,1,1, 'SIle', 'Kamat', 40224441219);

insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
values (angajati.nextval,1,8, 'Ye', 'Kanye', 40234143297);


insert into Top(id_top, denumire_top)
values (tops.nextval,'Best Romance');

insert into Top(id_top, denumire_top)
values (tops.nextval,'Best Overall');

insert into Top(id_top, denumire_top)
values (tops.nextval,'Best Action');

insert into Top(id_top, denumire_top)
values (tops.nextval,'Most Recommended');

insert into Top(id_top, denumire_top)
values (tops.nextval,'Funniest');
-------
insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Foarte Faina');

insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Buna');

insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Mediocra');

insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Slaba');

insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Groaznica');

insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Printre cele mai bune');

insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Printre cele mai rele');

insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Foarte Unica');

insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Design Slab');

insert into Review(id_review, descriere_review)
values (reviews.nextval, 'Animatie buna');

insert into Cumparator(id_cumparator, nume, prenume, varsta)
values (cumparatori.nextval, 'Ghinea', 'Silviu', 23);

insert into Cumparator(id_cumparator, nume, prenume, varsta)
values (cumparatori.nextval, 'Florica', 'Nwo', 24);

insert into Cumparator(id_cumparator, nume, prenume, varsta)
values (cumparatori.nextval, 'Tataee', 'Bug', 43);

insert into Cumparator(id_cumparator, nume, prenume, varsta)
values (cumparatori.nextval, 'Maresalu', 'Antonio', 29);

insert into Cumparator(id_cumparator, nume, prenume, varsta)
values (cumparatori.nextval, 'Pican', 'Antonio', 31);

insert into Cumparator(id_cumparator, nume, prenume, varsta)
values (cumparatori.nextval, 'Goku', 'Saiyan', 42);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 1, 1, 2, 'Genshin Impact', 20);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 1, 3, 2, 'Big Adventure', 25);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 2, null, 3, 'Re:Zero', 18);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 2, null, 1, 'Horimiya', 22);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 3, 2, 3, 'Ian si Azteca', 29);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 5, null, 4, 'Dragon Ball Z', 26);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 2, 4, 5, 'Last Airbender', 21);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 5, 5, 6, 'Worst Date', 31);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 5, null, 4, 'Best Date', 31);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 4, null, 3, 'Worst Date', 37);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 7, null, 3, 'New Stuff', 33);

insert into ComicBook(id_comic_book, id_comic_store, id_top, id_cumparator, nume, pret)
values (comics.nextval, 8, null, null, 'AA problems', 42);

insert into Vinde(id_angajat, id_comic_book)
values(1,3);

insert into Vinde(id_angajat, id_comic_book)
values(2,4);

insert into Vinde(id_angajat, id_comic_book)
values(1,5);

insert into Vinde(id_angajat, id_comic_book)
values(1,1);

insert into Vinde(id_angajat, id_comic_book)
values(2,6);

insert into Vinde(id_angajat, id_comic_book)
values(3,3);

insert into Vinde(id_angajat, id_comic_book)
values(3,6);

insert into Vinde(id_angajat, id_comic_book)
values(4,1);

insert into Vinde(id_angajat, id_comic_book)
values(5,8);

insert into Vinde(id_angajat, id_comic_book)
values(22,5);

insert into Primeste(id_review,id_comic_book)
values(1,1);

insert into Primeste(id_review,id_comic_book)
values(2,2);

insert into Primeste(id_review,id_comic_book)
values(3,4);

insert into Primeste(id_review,id_comic_book)
values(4,6);

insert into Primeste(id_review,id_comic_book)
values(5,8);

insert into Primeste(id_review,id_comic_book)
values(6,9);

insert into Primeste(id_review,id_comic_book)
values(7,10);

insert into Primeste(id_review,id_comic_book)
values(8,3);

insert into Primeste(id_review,id_comic_book)
values(9,5);

insert into Primeste(id_review,id_comic_book)
values(10,7);


insert into Ofera(id_review, id_cumparator)
values(2,5);

insert into Ofera(id_review, id_cumparator)
values(1,4);

insert into Ofera(id_review, id_cumparator)
values(3,1);

insert into Ofera(id_review, id_cumparator)
values(4,2);

insert into Ofera(id_review, id_cumparator)
values(10,3);

insert into Ofera(id_review, id_cumparator)
values(9,6);

insert into Ofera(id_review, id_cumparator)
values(5,3);

insert into Ofera(id_review, id_cumparator)
values(6,3);

insert into Ofera(id_review, id_cumparator)
values(7,3);

insert into Ofera(id_review, id_cumparator)
values(9,4);

--select * from angajat
--select * from comicbook
--select * from comicstore
--select * from joburi
--select * from top
--select * from Review
--select * from Cumparator
--select * from vinde
--select * from primeste
--select * from ofera
----exercitii 
--6 Aflati toti angajatii din magazine si codul acestor magazine
create or replace procedure ang_si_magazine 
as
    type vector is varray(50) of ComicStore.id_comic_store%type;
    type vector_2 is varray(50) of Angajat.nume%type;
    type table_1 is table of vector_2 index by pls_integer;
    
    cstore vector := vector();
    cangajat table_1;
    chk number(1) := 0;
begin
    select id_comic_store
    bulk collect into cstore
    from ComicStore;
    
    if cstore.count < 3 then 
        RAISE_APPLICATION_ERROR(-20099, 'Prea putine magazine!');
    end if;
    
    for i in 1..cstore.count loop
        select nume
        bulk collect into cangajat(i)
        from Angajat
        join ComicStore on Angajat.id_comic_store = ComicStore.id_comic_store
        where ComicStore.id_comic_store = cstore(i);
        dbms_output.put_line('Id-ul magazinului:' || cstore(i));
        for j in 1..cangajat(i).count loop
            dbms_output.put_line(cangajat(i)(j));
            end loop;
    end loop;
end ang_si_magazine;
/
set serveroutput on;
execute ang_si_magazine;

--7 Afisati numele tuturor revistelor avute cat si revistele ce contin in nume un anumit cuvant dat si care au pretul mai mare decat un pret dat
create or replace procedure comics_ex(p_cod comicbook.pret%type, p_cuvant in varchar2) 
as
cursor cursor1 is 
    select * from ComicBook;

cursor cursor2 (v_pret comicbook.pret%type, v_cuvant_cheie varchar2) is
    select * from comicbook
    where pret > v_pret
    and nume like '%'  || v_cuvant_cheie ||  '%';
    
comic comicbook%rowtype;
begin
    dbms_output.put_line('Toate revistele sunt: ');
    open cursor1;
    loop
        fetch cursor1 into comic;
        exit when cursor1%notfound;
        dbms_output.put_line('Numele: ' || comic.nume);
    end loop;
    close cursor1;
    
    dbms_output.put_line('Revistele cautate dupa nume si pret sunt: ');
    open cursor2(p_cod,p_cuvant);
    loop
        fetch cursor2 into comic;
        exit when cursor2%notfound;
        dbms_output.put_line('Pretul este: ' || comic.pret || ' si numele este ' || comic.nume);
    end loop;
    close cursor2;
end comics_ex;
/

begin
   comics_ex(29,'Date');
end;
    
--8 Pentru un id dat al unei reviste returnati pretul acesteia si afisati datele asociate ei
create or replace function reviste(p_id_comic comicbook.id_comic_book%type, lungime number) return number is
v_pret comicbook.pret%type;
v_comic_name comicbook.nume%type;
v_angajat_nume angajat.nume%type;
counter number;

pret_prea_mare exception;
nume_scurt exception;

begin
    select cb.pret, cs.nume_store, a.nume
    into v_pret, v_comic_name, v_angajat_nume
    from comicbook cb
    join comicstore cs on cb.id_comic_store=cs.id_comic_store
    join angajat a on cs.id_comic_store=a.id_comic_store
    where cb.id_comic_book=p_id_comic;
    
    if length(v_angajat_nume) < lungime then
        raise nume_scurt;
    end if;
    
    if v_pret > 40 then
        raise pret_prea_mare;
    end if;
    
    dbms_output.put_line('Numele magazinului este: ' || v_comic_name);
    dbms_output.put_line('Numele angajatului asociat este: ' || v_angajat_nume);
    dbms_output.put_line('Pretul pentru comic bookul cu id ul: ' || p_id_comic || ' este: ');
    
    return v_pret;
    
exception
    when NO_DATA_FOUND then
         RAISE_APPLICATION_ERROR(-20008, 'Nu exista comic-ul cu id ul dat');
    
    when pret_prea_mare then 
         RAISE_APPLICATION_ERROR(-20007, 'Pretul dat este prea mare');
    
    when nume_scurt then 
         RAISE_APPLICATION_ERROR(-20009, 'Numele este prea scurt!');
    
    when TOO_MANY_ROWS then 
         RAISE_APPLICATION_ERROR(-20006, 'Mai multe reviste!');
         
         
end reviste;
/
set serveroutput on;
select reviste(11) from dual;

begin
   dbms_output.put_line(reviste(9,2));
end;
/


--9 Aflati jobul avut de un angajat care lucreaza la un comic store care are o anumita revista ce se afla intr-un top cu titlul ce contine "Romance"
create or replace procedure job_avut(id_angajat_dat angajat.id_angajat%type)
is
    denumire_job joburi.nume_job%type;
begin
    select jb.nume_job 
    into denumire_job
    from joburi jb
    join angajat a on a.id_job = jb.id_job
    join comicstore cs on a.id_comic_store = cs.id_comic_store
    join comicbook cb on cs.id_comic_store = cb.id_comic_store
    join top tp on cb.id_top = tp.id_top
    where tp.denumire_top like '%Romance%' and a.id_angajat = id_angajat_dat;
    
    dbms_output.put_line('Jobul avut de angajatul cu id dat este: ' || denumire_job);
exception
    when NO_DATA_FOUND then
        RAISE_APPLICATION_ERROR(-20010, 'Nu s-au gasit joburi pe care lucreaza angajatul cu id-ul dat!');

end job_avut;
/

begin
    job_avut(6);
end;

--10 Creati un trigger care nu ne permite modificarea tabelului angajat in ziua de luni si duminica sau daca nu ne aflam in intervalul orar 8 -17
create or replace trigger actualizare_tabel
    before insert or update or delete on angajat
begin
if (to_char(sysdate,'D') = 1) or (to_char(sysdate,'D') = 2) or (to_char(sysdate,'HH24') not between 8 and 17)
then
    RAISE_APPLICATION_ERROR(-20010, 'Nu puteti actualiza tabelul!');
end if;
end;
/

--insert into Angajat(id_angajat, id_job, id_comic_store, nume, prenume, telefon)
--values (angajati.nextval,2,5, 'Surugiu', 'Tanya', 40277752711);
--drop trigger actualizare_tabel

--11 Creati un trigger care nu ne lasa sa modificam pretul revistelor daca diferenta dintre pretul vechi si cel nou este mai mica de 15
create or replace trigger actualizare_pret
    before update of pret on comicbook
    for each row
declare
    pret_obligatoriu exception;
begin
    if :old.pret - :new.pret < 15 then
        raise pret_obligatoriu;
    end if;
exception
    when pret_obligatoriu then
        RAISE_APPLICATION_ERROR(-20010, 'Pretul este prea mic! - NU AM ACTUALIZAT PRETUL');
end;
/

--update comicbook
--set pret = 24
--where id_comic_book = 2;
--drop trigger actualizare_pret

--12 Creati un trigger care nu ne permite crearea unor tabele noi in baza de date vinerea si sambata sau daca numele acestuia este fie prea mic < 2, fie prea mare > 10
create or replace trigger actualizare_database
before create on schema
declare
nume_gresit exception;
data_gresita exception;
begin
    if (to_char(sysdate,'D') between 6 and 7)
    then 
        raise data_gresita;
    elsif length(ora_dict_obj_name) < 2 or length(ora_dict_obj_name) > 10
    then
        raise nume_gresit;
    end if;
    
    exception
        when nume_gresit then
            RAISE_APPLICATION_ERROR(-20010, 'Numele introdus este prea scurt sau prea lung - incorect!');
        when data_gresita then
            RAISE_APPLICATION_ERROR(-20009, 'Data cand s-a dorit introducerea tabelului este invalida');
            
end;
/

--create table a(id number);
--drop trigger actualizare_database

--13
create or replace package pachet_13 as
    procedure ang_si_magazine;
    procedure comics_ex(p_cod comicbook.pret%type, p_cuvant in varchar2);
    function reviste(p_id_comic comicbook.id_comic_book%type, lungime number) return number;
    procedure job_avut(id_angajat_dat angajat.id_angajat%type);
end pachet_13;
/

create or replace package body pachet_13 as
    procedure ang_si_magazine 
as
    type vector is varray(50) of ComicStore.id_comic_store%type;
    type vector_2 is varray(50) of Angajat.nume%type;
    type table_1 is table of vector_2 index by pls_integer;
    
    cstore vector := vector();
    cangajat table_1;
    chk number(1) := 0;
begin
    select id_comic_store
    bulk collect into cstore
    from ComicStore;
    
    if cstore.count < 3 then 
        RAISE_APPLICATION_ERROR(-20099, 'Prea putine magazine!');
    end if;
    
    for i in 1..cstore.count loop
        select nume
        bulk collect into cangajat(i)
        from Angajat
        join ComicStore on Angajat.id_comic_store = ComicStore.id_comic_store
        where ComicStore.id_comic_store = cstore(i);
        dbms_output.put_line('Id-ul magazinului:' || cstore(i));
        for j in 1..cangajat(i).count loop
            dbms_output.put_line(cangajat(i)(j));
            end loop;
    end loop;
end ang_si_magazine;

     procedure comics_ex(p_cod comicbook.pret%type, p_cuvant in varchar2) 
as
cursor cursor1 is 
    select * from ComicBook;

cursor cursor2 (v_pret comicbook.pret%type, v_cuvant_cheie varchar2) is
    select * from comicbook
    where pret > v_pret
    and nume like '%'  || v_cuvant_cheie ||  '%';
    
comic comicbook%rowtype;
begin
    dbms_output.put_line('Toate revistele sunt: ');
    open cursor1;
    loop
        fetch cursor1 into comic;
        exit when cursor1%notfound;
        dbms_output.put_line('Numele: ' || comic.nume);
    end loop;
    close cursor1;
    
    dbms_output.put_line('Revistele cautate dupa nume si pret sunt: ');
    open cursor2(p_cod,p_cuvant);
    loop
        fetch cursor2 into comic;
        exit when cursor2%notfound;
        dbms_output.put_line('Pretul este: ' || comic.pret || ' si numele este ' || comic.nume);
    end loop;
    close cursor2;
end comics_ex;
    
    function reviste(p_id_comic comicbook.id_comic_book%type, lungime number) return number is
v_pret comicbook.pret%type;
v_comic_name comicbook.nume%type;
v_angajat_nume angajat.nume%type;
counter number;

pret_prea_mare exception;
nume_scurt exception;

begin
    select cb.pret, cs.nume_store, a.nume
    into v_pret, v_comic_name, v_angajat_nume
    from comicbook cb
    join comicstore cs on cb.id_comic_store=cs.id_comic_store
    join angajat a on cs.id_comic_store=a.id_comic_store
    where cb.id_comic_book=p_id_comic;
    
    if length(v_angajat_nume) < lungime then
        raise nume_scurt;
    end if;
    
    if v_pret > 40 then
        raise pret_prea_mare;
    end if;
    
    dbms_output.put_line('Numele magazinului este: ' || v_comic_name);
    dbms_output.put_line('Numele angajatului asociat este: ' || v_angajat_nume);
    dbms_output.put_line('Pretul pentru comic bookul cu id ul: ' || p_id_comic || ' este: ');
    
    return v_pret;
    
exception
    when NO_DATA_FOUND then
         RAISE_APPLICATION_ERROR(-20008, 'Nu exista comic-ul cu id ul dat');
    
    when pret_prea_mare then 
         RAISE_APPLICATION_ERROR(-20007, 'Pretul dat este prea mare');
    
    when nume_scurt then 
         RAISE_APPLICATION_ERROR(-20009, 'Numele este prea scurt!');
    
    when TOO_MANY_ROWS then 
         RAISE_APPLICATION_ERROR(-20006, 'Mai multe reviste!');
         
         
end reviste;

    procedure job_avut(id_angajat_dat angajat.id_angajat%type)
is
    denumire_job joburi.nume_job%type;
begin
    select jb.nume_job 
    into denumire_job
    from joburi jb
    join angajat a on a.id_job = jb.id_job
    join comicstore cs on a.id_comic_store = cs.id_comic_store
    join comicbook cb on cs.id_comic_store = cb.id_comic_store
    join top tp on cb.id_top = tp.id_top
    where tp.denumire_top like '%Romance%' and a.id_angajat = id_angajat_dat;
    
    dbms_output.put_line('Jobul avut de angajatul cu id dat este: ' || denumire_job);
exception
        
    when NO_DATA_FOUND then
        RAISE_APPLICATION_ERROR(-20010, 'Nu s-au gasit joburi pe care lucreaza angajatii cu id-ul dat!');
    
end job_avut;

end pachet_13;
/

exec pachet_13.ang_si_magazine;

exec pachet_13.comics_ex(29,'Date');

select pachet_13.reviste(12,8) from dual;

exec pachet_13.job_avut(242);