<!-- Preview = Ctrl + Maj + V on VsCode-->


# Utiliser fonction asynchrone
* #### Fonctionnement de async/await
 
 La programmation asynchrone est une technique qui permet à un programme de démarrer une tâche à l'exécution potentiellement longue et, au lieu d'avoir à attendre la fin de la tâche, de pouvoir continuer à réagir aux autres évènements pendant l'exécution de cette tâche. Une fois la tâche terminée, le programme en reçoit le résultat. (Promesse)
```bash
# Fichier Html
## Nous retournerons la valeur de résultat directement dans mon html via textContent.
    <div id="result">
        Async function example
    </div>

# Fichier JS
## On veut faire une addition des résultats de deux fonctions. 
### Utilisation du préfixe async TOUJOURS devant le nom de ma fonction.

    async function getNumber1() {
        return 5; # Valeur de retour = 5.
    }

    async function getNumber2() {
        return 8; # Valeur de retour = 8.
    }

### Utilisation du await devant ma réponse asynchrone attendu -> devant mes fonction async.
    async function compute(){
        return await getNumber1() + await getNumber2() # Valeur de retour = 5 + 8.
    }

### Utilisation du then(). Permet de récupérer les données une fois qu'elles sont transmises.
    compute().then(function(reponse) {
        result.textContent = reponse # La valeur de retour dans mon Html est de 13.
    })

#### Votre code asynchrone est maintenant fonctionnel

```

****
* ##### Appliquer une structure de code plus simple et plus propre. 

```bash

## Création de mes deux fonctions asynchrones sous forme de fonctions fléchées.

const getNumber1 = async () => 5;   
const getNumber2 = async () => 8;

## Création de ma fonction asynchrone qui additionne 2 paramètres.(a,b)
const compute = async (a,b) => await a + await b;


## Lancement de ma fonction avec en paramètres getNumber1(),getNumber2().
compute(getNumber1(), getNumber2())
    .then( reponse => result.textContent = reponse) ## Concaténation de .then(réponse => contenu html = réponse)

```


*********
* ##### Gérer les erreurs de promesses. 

Il est possible d'utiliser la méthode catch() afin de gérer une erreur de retour de notre promesse.
```bash

# Reprenons la fonction ci-dessus.
## Application de la méthode catch()

compute(getNumber1(), getNumber2())
    .then( reponse => result.textContent = reponse)
    .catch(err =>{ console.log(err) })
#

```

