# But

* Développer un formulaire de connexion avec 3 champs (`email`, `password` et `remember me`) en HTML5
* Vérifier les données saisies en JavaScript 

# Architecture du projet

![shipping_cart_architecture](shipping_cart_architecture.png)

* __Navigateur__ : Permet de consulter et d'afficher le rendu du projet (Ex : Chrome, Firefox, Internet Explorer, ...)
    * _Navigateur à utiliser : Chrome_
* __Serveur Web__ : Permet de servir des requêtes respectant le protocole HTTP (Ex : [Apache HTTP](https://httpd.apache.org/), [NGINX](http://nginx.org), [Node.js](https://nodejs.org), ...)
    * _Serveur à utiliser : NGINX_
* __Base de données__ : Permet de stocker et de partager des données (Ex : [MySQL](https://www.mysql.fr), [Oracle Database](http://www.oracle.com/fr/database/overview/index.html), [MariaDB](https://mariadb.org), ...)
    * _Base de données utilisée pour conserver le panier : [Window.sessionStorage](https://developer.mozilla.org/fr/docs/Web/API/Window/sessionStorage)_

# Flow du paiement



# Mise en place de l'environnement
## Récupération du projet sous Github

```
git clone https://github.com/aicfr/shopping-cart.git c:/web/html
```

## Test de l'application
### Lancement de NGINX

```
cmd.exe

cd c:\opt\nginx

# Start
nginx.exe

# Stop (Dans une autre fenêtre de cmd.exe)
nginx.exe -s stop
```

### Lancement de l'application

Tester l'application : <http://localhost>

![discdog](discdog.png)

# Développement
## Formulaire de "login"
### Spécifications du formulaire

Editer le fichier `checkout.html` et ajouter le code nécessaire à la création d'un formulaire de type "login". Celui-ci devra comporter les éléments suivant :

* Un champ permettant la saisie d'une adresse email (obligatoire)
* Un champ permettant la saisie d'un mot de passe (obligatoire)
* Une case à cocher "Se souvenir de moi"
* Un bouton de validation permettant d'accéder à la page des moyens de paiement (`choose.html`)

##### Les mots clés

* HTML5
* `<form>`, `method` et `action`
* `<label>`
* `<input>` de type `email`, `password`, `checkbox` et `submit`
* `required`
* `POST`

##### Exemple

![form](form.png)

### Validation des données

Editer le fichier `checkout.html` et ajouter le bloc ci-dessous après la balise `</form>`.

Dans cette partie nous souhaitons :

* Récupérer les valeurs saisies dans les champs `email` et `password`
* Puis valider que le couple `email` / `password` existe bien (Ex : foo@foo.com / sa)

```
<script>
    var email = // Get email value ;
    var password = // Get password value ;

    var login = function () {
    // Verify login / password
    };

    email.addEventListener('change', login, false);
    password.addEventListener('change', login, false);

    var form = document.getElementById('loginForm');
    form.addEventListener('submit', function () {
        login();
        if (!this.checkValidity()) {
            event.preventDefault();
        }
    }, false);
</script>
```

##### Les mots clés

* `getElementById(...)`
* `setCustomValidity(...)`
* `if` et `else`
* `value`
* `&&`