# Noé Zwissig analyse

# First mind idea on paper
## V1
<img src="./img/V1.jpg" alt="V1" style=" margin-left: 50px; height: 500px; transform: rotate(90deg);"/>

## V2
<img src="./img/V2.jpg" alt="V2" style=" margin-left: 50px; height: 500px; transform: rotate(90deg);"/>

## V3
<img src="./img/V3.jpg" alt="V3" style=" margin-left: 50px; height: 500px; transform: rotate(90deg);"/>

# MCD V1.0
<img src="./img/SQL1Prj1MCDNoéZwissig.jpg" alt="V1" style=" margin-left: 50px; height: 500px;"/>

# MCD V2.0
<img src="./img/SQL1Prj1MCDNoéZwissigV2.jpg" alt="V1" style=" margin-left: 50px; height: 500px;"/>

## fix inside the v2:
Update the person table to add the status enum inside.\
Correct the "note" table as "grade" and the "note" as result.\
add startTime in lesson

# Decision and explanation


# Question

Est-ce que tous les élève au sein d'un classe on FORCEMENT les même leçon ?
: OUI

Quel info voulez-vous pour les élève ?
: horaire par semestre
nom
prénom
adresse
email
téléphone
statut -> en cours, terminé, abandonné
  
Quel info voulez-vous pour les enseignants ?
: planning
nom
prénom
adresse
email
téléphone
statut -> retraite,pas de cours, en fonction
iban

Quel info voulez-vous pour les cours ?
: nom
description
semestre ou il est donnée (évolutif)
horaire
note
semestre 

Quel info pour les notes ?
: nom
description
Date de réalisation

Avez-vous des cas spéciaux que vous voulez que nous tenions compte ? 
: aucun 

Des semaines spécial ?
: non

Des appuis ?
: non aucun

Des fonctionnalité que vous voulez que la future application soit capable de faire ?
: aucune

Seulement 3 Entité ? par de salle, bâtiment ou autre ? 
: salle -> tout les cours sont dans la même salle pour une classe (peut changer) 
  
Voulez-vous un historique ?
: oui

Comment fonctionne les promotion ? trimestre semestre libre ? 
: par trimestre et moyenne de toute les notes supérieur a 4 et module validé

Est-ce que vous voulez que les conditions de promotion soie stockée dans la db ? 
: oui stocké les fonction
et garder un historique

Est-ce que le prof est déterminer par la branche ou par la leçon ?  
: toujours le même prof par branche
mais peut changé année après année

Voulez-vous pouvoir attribué certaine chose à une période spécifique ? (devoir)
: NON

Note de discusion :
: l'horaire sera générer 
chaque trimestre est parfaitement identique sur toute les semaine  qui le compose.(semaine type)
un élève peut devenir enseignant
