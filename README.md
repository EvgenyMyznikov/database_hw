# Домашнее задание к занятию «Базы данных» - Evgeny Myznikov

### Задание 1

1.CREATE TABLE public."Branch address" (
	id int4 NOT NULL GENERATED ALWAYS AS IDENTITY,
	address varchar(100) NOT NULL,
	CONSTRAINT branch_address_pk PRIMARY KEY (id)
);
2.CREATE TABLE public."Employees" (
	id int4 NOT NULL GENERATED ALWAYS AS IDENTITY,
	salary money NOT NULL,
	CONSTRAINT employees_pk PRIMARY KEY (id),
	CONSTRAINT job_title_fk FOREIGN KEY (id) REFERENCES public."Job title"(id) ON DELETE CASCADE ON UPDATE CASCADE,
	CONSTRAINT person_fk FOREIGN KEY (id) REFERENCES public."Person"(id) ON DELETE CASCADE ON UPDATE CASCADE,
	CONSTRAINT project_fk FOREIGN KEY (id) REFERENCES public."Project assigned to"(id) ON DELETE CASCADE ON UPDATE CASCADE
);
3.CREATE TABLE public."Job title" (
	id int4 NOT NULL GENERATED ALWAYS AS IDENTITY,
	"job title" varchar(100) NOT NULL,
	CONSTRAINT job_title_pk PRIMARY KEY (id)
);
4.CREATE TABLE public."Person" (
	id int4 NOT NULL GENERATED ALWAYS AS IDENTITY,
	"first name" varchar(30) NOT NULL,
	"middle names" varchar(30) NOT NULL,
	"last name" varchar(50) NOT NULL,
	"date of employment" date NOT NULL,
	CONSTRAINT person_pk PRIMARY KEY (id)
);
5.CREATE TABLE public."Project assigned to" (
	id int4 NOT NULL GENERATED ALWAYS AS IDENTITY,
	"Project name" varchar(100) NOT NULL,
	CONSTRAINT project_pk PRIMARY KEY (id)
);
6.CREATE TABLE public."Structural subdivision" (
	id int4 NOT NULL GENERATED ALWAYS AS IDENTITY,
	"subdivision name" varchar(100) NOT NULL,
	CONSTRAINT structural_subdivision_pk PRIMARY KEY (id),
	CONSTRAINT branch_address_fk FOREIGN KEY (id) REFERENCES public."Branch address"(id) ON DELETE CASCADE ON UPDATE CASCADE,
	CONSTRAINT employees_fk FOREIGN KEY (id) REFERENCES public."Employees"(id) ON DELETE CASCADE ON UPDATE CASCADE,
	CONSTRAINT subdivision_type_fk FOREIGN KEY (id) REFERENCES public."Structural subdivision type"(id) ON DELETE CASCADE ON UPDATE CASCADE
);
7.CREATE TABLE public."Structural subdivision type" (
	id int4 NOT NULL GENERATED ALWAYS AS IDENTITY,
	"Subdivision type" varchar(100) NOT NULL,
	CONSTRAINT subdivision_type_pk PRIMARY KEY (id)
);