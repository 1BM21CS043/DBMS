create database 1bm21cs043_Insurance;

create table person(
driver_id varchar(10),
name varchar(20),
address varchar(30),
primary key(driver_id)
);

create table car(
reg_num varchar(10),
model varchar(10),
year int,
primary key(reg_num)
);

create table accident(
report_num int,
accident_date date,
location varchar(20),
primary key(report_num)
);

create table owns(
driver_id varchar(10),
reg_num varchar(10),
primary key(driver_id,reg_num),
foreign key(driver_id) references person(driver_id),
foreign key(reg_num) references car(reg_num)
);

create table participated(
driver_id varchar(10),
reg_num varchar(10),
report_num int,
damage_amount int,
primary key(driver_id          ,reg_num,report_num),
foreign key(driver_id) references person(driver_id),
foreign key(reg_num) references car(reg_num),
foreign key(report_num) references accident(report_num)
);

insert into accident values(11,'2003-01-01','Mysore Road');
insert into accident values(12,'2004-02-02','south end circle');
insert into accident values(13,'2008-02-17','Bull temple road');
insert into accident values(14,'2004-03-05','kanakpura Road');
insert into accident values(15,'2008-02-17','Mysore road');

insert into person values('A01','Richard','Srinivas nagar');
insert into person values('A02','Pradeep','Rajaji nagar');
insert into person values('A03','Smith','Ashok nagar');
insert into person values('A04','Venu','N R Colony');
insert into person values('A05','Jhon','Hanumanth Nagar');

insert into car values('KA052250','Indica','1990');
insert into car values('KA031181','Lancer','1957');
insert into car values('KA095477','Toyota','1998');
insert into car values('KA053408','Honda','2008');
insert into car values('KA041702','Audi','2005');

insert into owns values('A01','KA052250');
insert into owns values('A02','KA031181');
insert into owns values('A03','KA095477');
insert into owns values('A04','KA053408');
insert into owns values('A05','KA041702');

insert into participated values('A01','KA052250',11,10000);
insert into participated values('A02','KA053408',12,50000);
insert into participated values('A03','KA095477',13,25000);
insert into participated values('A04','KA031181',14,3000);
insert into participated values('A05','KA041702',15,5000);

update participated set damage_amount=25000 
where reg_num='KA053408' and report_num=12;

select count(distinct driver_id)CNT
from participated a,accident b
where a.report_num=b.report_num and b.accident_date like '%08%';

insert into accident values(16,'2008-03-08','Domlur');

select*from accident;

select accident_date,location 
from accident;

select driver_id
from participated
where damage_amount>=25000;

select*from participated order by damage_amount desc;

select avg(damage_amount) 
from (participated); 

delete from participated
where damage_amount<(select avg (damage_amount) from participated);

select*from car order by year asc;

select count(report_num)
from car c, participated p
where c.reg_num=p.reg_num and c.model='Lancer';

select count(distinct driver_id)CNT
from participated A, accident b
where a.report_num=b.report_num and b.accident_date like'__08%';

select name from person p,
participated part where p.driver_id=part.driver_id and damage_amount>(select avg(damage_amount) from participated);

select MAX(damage_amount)
from participated;

/*switch off safe update for the next queiry*/

delete from participated 
where damage_amount<(select p.damage_amount from(select avg(damage_amount) as damage_amount from participated) p);


















