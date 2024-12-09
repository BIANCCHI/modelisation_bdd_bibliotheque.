# modelisation_bdd_bibliotheque.
1.analyse des besoins
[Document sans titre.pdf](https://github.com/user-attachments/files/18068564/Document.sans.titre.pdf)



2.Modelisation relationnelle
<img width="1088" alt="Capture d’écran 2024-12-05 à 15 26 27" src="https://github.com/user-attachments/assets/2a78de11-ddc9-491d-8a62-09baa096f9d0">
<img width="1172" alt="Capture d’écran 2024-12-05 à 15 26 08" src="https://github.com/user-attachments/assets/27edc8d8-33e9-4322-9cd4-1420afbce72f">







4.5.6:: Création de la base de données,Insertion de données,Requêtes avancées 
create database bibliotheque;
use bibliotheque;
create table livre
(
	id_livre int not null,
    titre varchar(20) not null,
    auteur char(20) not null,
    isbn varchar(20) null,
    nombre_exemplaires double(6,2),
    constraint pk_id_livre primary key(id_livre)
);
insert into livre values(101,"la maison d'à coté","Ingenieur Kermelis","extrememeta",3);
insert into livre values(102,"QSPA","biancci","XM",5);
insert into livre values(103,"genie logociel","joseph","LMR",10);



select * from livre;
create table membre
(
	id_membre int not null,
    nom varchar(30) not null,
    prenom char(20) null,
    adresse char(25) null,
    telephone varchar(10) not null,
	constraint pk_id_reservation primary key(id_membre)
);
insert into membre values(201,"biancci","lourd","france","+33787676");
insert into membre values(202,"kermelis","ntumba","rdc","+243987676");
insert into membre values(203,"ismael","malonda","canada","+13787676");
select * from membre;

create table emprute
(
	id_emprunte int not null,
    id_livre int not null,
    id_membre int not null,
    date_emprunt date null,
    date_retour date null,
    constraint pk_id_emprunte primary key(id_emprunte),
    constraint fk_livre_emprunt foreign key(id_livre) references livre(id_livre),
    constraint fk_membre_emprunt foreign key(id_membre) references membre(id_membre)
);
insert into emprute values(301,102,203,'2024-12-10','2024-12-09');
insert into emprute values(302,101,202,'2024-09-13','2024-12-11');
insert into emprute values(303,103,201,'2024-04-07','2024-06-09');

select * from emprute;

create table reservation
(
	id_reservation int not null,
    id_livre int not null,
	id_membre int not null,
    date_reservation date null,
	constraint pk_id_reservation primary key(id_reservation),
    constraint fk_livre_reserv foreign key(id_livre) references livre(id_livre),
    constraint fk_membre_reserv foreign key(id_membre) references membre(id_membre)
);
insert into reservation values(401,103,201,'2024-12-13');
insert into reservation values(402,101,203,'2024-09-12');
insert into reservation values(403,102,202,'2024-04-13');
select * from reservation;




7.Rapport final 
Maintien de l'intégrité des données : La gestion des clés primaires et étrangères a été essentielle pour garantir que les relations entre les tables étaient respectées.
Insertion de données cohérentes : Lors de l'insertion des données, nous avons dû nous assurer que les informations sur les livres, les membres, les emprunts et les réservations étaient réalistes et diversifiées pour tester efficacement les fonctionnalités.
Requêtes complexes : Les jointures entre les tables ont été nécessaires pour obtenir des informations complexes, mais cela a ajouté de la complexité aux requêtes SQL.









8.Conclusion
Ce projet de gestion de bibliothèque nous a permis de concevoir une base de données relationnelle solide et de maîtriser l'utilisation des requêtes SQL pour gérer les livres, les membres, les emprunts et les réservations. Grâce à l'application des formes normales, nous avons évité les anomalies de données et avons optimisé la gestion des informations.





