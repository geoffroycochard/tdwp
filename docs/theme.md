# Theme developpement

## Principe

Un thème wordpress regroupe un design et des fonctionnalités spécifiques pour le site.
On peut profiter de toute l'API Wordpress. (templates, template tags, loops)

__[Source officiel](https://codex.wordpress.org/Theme_Development)__

## Composition d'un thème

Un thème doit composer d'au moins deux fichiers pour être reconnu par Wordpress
    
    - style.css
     /*
     Theme Name: Le thème de test
     Author: Midnight Falcon
     Author URI: http://monsiteweb.com
     Description: Notre premier thème WordPress !
     */
     
 * function.php
 
## Ressources
    
 * [Theme part](resources/Theme.pdf)
 * [Officiel documentation](https://codex.wordpress.org/Theme_Development)
 * [Voir l'anatomie d'un thème wordpress](https://cdn.yoast.com/app/uploads/2011/01/anatomy-wordpress-yoast.png)

## Exercice

### Création du thème

[A partir de ce package](resources/html5up-massively.zip), créer un theme.

#### Répertoire

Créer le répertoire qui va accueillir notre thème dans ````wp-content/theme```` avec le nom du theme "massively"

 * Créer les fichiers ```style.css``` ainsi qu'un ```index.php```
 * Intégrer le template en le découpant avec la logique d'un thème wordpress (Header, footer, etc...)
 * Insérer les styles / scripts avec les functions ```wp_enqueue_*```
 * Mappé un menu, deux zones de pied de pages afin de les rendre dynamiques
 
### Ajouter un post type "concert"

 