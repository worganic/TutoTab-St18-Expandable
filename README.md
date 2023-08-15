# WorganicTabV1 / v18 : Table/Expendable

This project was generated with [Angular CLI](https://github.com/angular/angular-cli) version 16.1.1.

## Development server

Run `ng serve` for a dev server. Navigate to `http://localhost:4200/`. The application will automatically reload if you change any of the source files.


## Development server json

Run `json-server --watch db.json` for a dev server. Navigate to `http://localhost:3000/`.

## Code scaffolding

Run `ng generate component component-name` to generate a new component. You can also use `ng generate directive|pipe|service|class|guard|interface|enum|module`.

## Build

Run `ng build` to build the project. The build artifacts will be stored in the `dist/` directory.

## Get clone 
> https://github.com/worganic/TutoTab-St18-create.git
> npm install
> cd .\worganic-tab-v1\
> ng serve

## Project :
v18 - Tableau options -> Expendable

    ** Exemple injection : Section exemple injected =>
    --------------------------------------------------
        - Création de la section injected (component):

        - Ajout de la route injected
            >> path: 'injected', :
            \src\main.ts
        - Ajout dans le menu :
            \src\app\app.component.html

    ** Mise en place de l'expandable pour le tableau :
    --------------------------------------------------
    - Mise à jour de la db.json

    - Modification du tableau pour ajouter la zone expandable
        \src\app\shared\component\worg-table\worg-table.component.html
            Ajout de la zone expandable :
                <tr *ngIf="element.isExpand">
            Ajout du click pour activé l'expandable :
                (click)="element.isExpand = !element.isExpand"
            Ajout du nombre de colonne en tous :
                \src\app\shared\component\worg-table\worg-table.component.ts
                colonneCount: Number = 0;
            Modification dans la vue :-
                \src\app\shared\component\worg-table\worg-table.component.html
                <td [attr.colspan]="elementTotal" >

    - Ajout component WorgTableExpandableComponent
        \src\app\shared\component\worg-table\worg-table-expandable\worg-table-expandable.component.ts 

    - Ajout service ExpandableService pour intégré la liste des zone expandable :
        \src\app\component\expandableListe.ts

    - Ajout du componetn exapandable lié à Users :
        \src\app\component\users\expanded\expanded.component.ts

    - Mise en place la pause du timer si une ligne est expandable :
        \src\app\shared\component\worg-table\worg-table.component.ts
        >> expandable(element: any){
        Et changement du timer :
            >> startTimer(time1: number = this.timeLeft) {
            >> this.time = time1;

## Infos plus :
   
## Update

## Historique :
Avant -> v17 - Tableau options -> Pipe
Après -> v19 - Ajout bouton delete.

## Ressource :
    - promise :
    https://www.bennadel.com/blog/3835-returning-promises-from-async-await-functions-in-javascript.htm
    - récupération de methode dynamiquament :
    https://stackoverflow.com/questions/57086672/element-implicitly-has-an-any-type-because-expression-of-type-string-cant-b
    - Problème d'import avec string :
    https://github.com/webpack/webpack/issues/6680

## Abouts
created by Johann Loreau
create at 2023/07/29
Le project évolura suivant les remarques et conseils des visiteurs.