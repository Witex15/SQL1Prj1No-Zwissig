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





















# MLD

In this MLD something as been upgraded. The tables are now in plural. Some typo as also been corrected.

```mermaid
classDiagram
    people -- people_obtain_grades
    people_obtain_grades -- grades
    people -- people_participate_terms
    people_participate_terms -- terms

    people -- classes
    people -- addresses
    rooms -- addresses
    classes -- lessons
    lessons -- branches
    grades -- terms
    classes -- rooms
    branches -- grades
    
    class people{
        id_people NUMBER
        first_name TEXT
        last_name TEXT
        email TEXT
        phone_number TEXT
        iban TEXT
        status Enum(inProgress: 0, done: 1, aborted: 2, retired: 3, noLessons: 4, onDuty: 5)


        pk(id_people)
        fk(addresses_id)
        fk(classes_id)
    }
    class people_obtain_grades{
        id_people_grades NUMBER
        people_id NUMBER
        grades_id NUMBER
        
        pk(id_people_grades)
        fk(people_id)
        fk(grades_id)
    }
    class grades{
        id_grades NUMBER
        result TEXT
        name TEXT
        description TEXT
        done_date DATE
        effective_date DATE
        
        pk(id_grades)
        fk(branches_id)
        fk(terms_id)
    }
    class people_participate_terms{
        id_people_terms
        people_id NUMBER
        terms_id NUMBER
        
        pk(id_people_terms)
        fk(people_id)
        fk(terms_id)
    }
    class terms{
        id_terms NUMBER
        start_date DATE
        end_date DATE
        
        pk(id_terms)
    }
    class addresses{
        id_addresses NUMBER
        post_code NUMBER
        city TEXT
        street TEXT 
        number TEXT
        contry TEXT
        
        pk(id_addresses)
    }
    class rooms{
        id_rooms NUMBER
        name TEXT
        number TEXT
        
        pk(id_rooms)
        fk(classes_id)
        fk(addresses_id)
    }
    class classes{
        id_classes NUMBER
        name  TEXT
        
        pk(id_classes)
    }
    class lessons{
        id_lessons NUMBER
        duration NUMBER
        start_time TIME
        weekDay Enum(MONDAY: 0, TUESDAY: 1, WEDNESDAY: 2, THURSDAY: 3, FRIDAY: 4, SATURDAY: 5, SUNDAY: 6)
        
        pk(id_lessons)
        fk(classes_id)
        fk(branches_id)
    }
    class branches{
        id_branches NUMBER
        title TEXT
        description TEXT
        
        pk(id_branches)
    }
    class promotion_conditions{
        id_promotionConditions NUMBER
        function TEXT
        start_date DATE
        end_date DATE
        
        pk(id_promotionConditions)
    }
    
```
    
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