# WorganicTabV1 / v19 : Table/Button/deleted

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
> https://github.com/worganic/TutoTab-St19-create.git
> npm install
> cd .\worganic-tab-v1\
> ng serve

## Project :
v19 - Ajout bouton delete.

    - On déplace les dossiers lié à l'outil table dans le dossier worg-table
            \src\app\shared\component\worg-table
            \src\app\shared\component\worg-table\worg-pipes
            \src\app\shared\component\worg-table\worg-pagination
            \src\app\shared\component\worg-table\worg-expandable
        On modifi les liens des impots dans :
            \src\app\shared\component\worg-table\worg-table.component.ts
    - On rajoute la zone bouton :
            \src\app\shared\component\worg-table\worg-table.component.html
        >> ...(click)="buttonFct(column)"...
    - On ajoute les options à Users le type 'button':
            \src\app\component\users\users.component.ts
        >> listeColumns: any[] = [...
          {column: 'delete', columnTitle: 'Delete', type:'button', columnHidden: false},
    - Problème : l'expandable ce déclanche lorsqu'on clique sur le bouton.
        On va donc déplacé l'expandable dans certaine zone.

    - Ajout de l'eventEmitter :
        \src\app\shared\component\worg-table\worg-table.component.ts
            >> buttonFct(element: any){...
        On oubli pas de créé l'interface :
            >> export interface ModelExport {...
    - Ajout des data (Output) dans le fichier html de base (Users) :
        \src\app\component\users\users.component.html
            >> (action)="action($event)"
    - Ajout de la fct de reception des données :
        \src\app\component\users\users.component.ts
            >> action(data: any){...
    - On ajoute la fct delete au service Users :
        \src\app\shared\services\users.service.ts
            >> delUser(element: any) {...
    - On associe la fct à l'action (service/delete).
        \src\app\component\users\users.component.ts
            >> this._usersService.delUser(data['element']);

        [ On test et on vérifi bien que le bouton delete supprime bien l'element dans le fichier db.json. ]

    - On doit mettre à jour l'affichage sans l'element supprimé :
            >> buttonFct(element: any){...
                this.majDonnees();
            }

        [ Le système Expandable bloque le compteur, on doit donc résoudre le pb Expandable de suite.]

    - On ajoute 2 paramètres aux options :
        \src\app\component\users\users.component.ts
            >> 'expandabled': false,// Expandable actif.
            >> 'expandableCol': true,// false : exapandable si click sur la ligne // true : uniquement sur certaine colonne :  expandable: true
    - On modifie l'emplacement du click sur les td et on l'envoi vers une fonction :
        \src\app\shared\component\worg-table\worg-table.component.html
            >> ...(click)="expandableAction(element, column.expandable)"...
    - On crait une fonction pour testé les paramètres et lancé expandable si besoin :
       \src\app\shared\component\worg-table\worg-table.component.ts
            >> expandableAction(element: any, expandable: boolean = false){...
    - Pour résoudre le pb Pipe avec value undefined, on rajoute un test dans :
        \src\app\shared\component\worg-table\worg-pipes\tbPipe.pipe.ts
            >> ...if(value != undefined)...

    - Ajout du paramètre columnPriority pour les options des colonnes :
        \src\app\component\users\users.component.ts
            >> ...columnPriority:'5'...
            Option de 1 à 5
    - Ajout des css lié aux priorités :
        \src\app\shared\component\worg-table\worg-table.component.scss
    - Ajout des classes aux colonnes (titre/filtre/data).
        \src\app\shared\component\worg-table\worg-table.component.html
            >> ...{{ column?.columnPriority }}...


## Problème à résoudre :
    - Dans l'expandable, une donnée (bloc) peu ne pas être dispo, cela provoque une erreur console.
    - l'expandable ce déclanche lorsqu'on clique sur le bouton.
        On va donc déplacé l'expandable dans certaine zone.
    

## Infos plus :
   
## Update

## Historique :
Avant -> v18 - Tableau options -> Expendable
Après -> v20 - Tableau -> Button -> edit

## Ressource :
    - Button click :
        https://angular.io/guide/event-binding
    - Css hidden colonnes :
        https://phppot.com/css/automatic-column-hiding-using-css-in-responsive-table/

## Abouts
created by Johann Loreau
create at 2023/08/16
Le project évolura suivant les remarques et conseils des visiteurs.