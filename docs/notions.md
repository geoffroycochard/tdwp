# Notions indispensables

## Contexte wordpress / Template hiérarchie
__[Source officiel](https://codex.wordpress.org/fr:Hi%C3%A9rarchie_des_fichiers_mod%C3%A8les)__

Les fichiers modèles des thèmes constituent les pièces du puzzle que WordPress assemble pour afficher les pages de votre site. Certains modèles (les fichiers d'entête ou de pied de page, par exemple) sont utilisés pour toutes les pages générées ; d'autres ne sont utilisés que sous certaines circonstances.

> Quel fichier de modèle sera utilisé par WordPress pour afficher tel type de page ?

### Principe

WordPress utilise la Query String — information présente au sein de toute URL (lien) pointant sur votre site — pour décider quel modèle, ou ensemble de modèles, utiliser pour l'affichage de la page en question.

En premier lieu, WordPress compare chaque Query String aux différents types de requête — afin de repérer quel type de page (une page de recherche, une page de catégorie, la page d'accueil, etc.) doit être affiché.

Les fichiers modèles sont alors sélectionnés — et le contenu de la page est généré — selon la hiérarchie des modèles de WordPress présentée ici, en fonction de leur présence ou non dans le thème WordPress utilisé.

WordPress recherche les fichiers modèles possédant le nom précis attendu dans le répertoire du thème courant et utilise le premier fichier trouvé de la hiérarchie listé dans la section correspondant au type de page à afficher (cf. ci-dessous).

À l'exception du fichier modèle de base ```index.php``` qui doit être présent dans tout thème, les développeurs de thème sont libres de choisir s'ils veulent ou non implémenter ou non tel ou tel fichier modèle. Si WordPress ne trouve pas le premier fichier attendu pour le type de page dans la liste, il passe au fichier suivant de la hiérarchie. En dernier lieu, si aucun fichier n'a été trouvé, c'est le fichier ```index.php``` qui sera utilisé.

![Template hiérachie](img/Template_Hierarchy_2015.png)
[Télécharger l'image](img/Template_Hierarchy_2015.png)

### Exemple
i votre blog est à l'adresse http://example.com/wordpress/ et qu'un visiteur charge la page http://example.com/wordpress/, WordPress cherche un fichier de modèle appelé home.php et l'utilise pour générer la page. Si home.php n'existe pas, WordPress recherche un fichier appelé index.php dans le répertoire du thème et l'utilise alors pour générer la page.


## Marqueurs conditionnels
__[Source officiel](https://codex.wordpress.org/fr:Marqueurs_conditionnels)__

Les Marqueurs Conditionnels peuvent être utilisés dans vos Thèmes pour décider du contenu à afficher sur une page spécifique ou comment ce contenu doit être affiché en fonction de conditions que remplit cette page. Par exemple, si vous voulez insérer un texte particulier au-dessus d'une série d'Articles, mais seulement sur la page principale de votre blog, avec le Marqueur Conditionnel ```is_home()```, cela devient facile.

Ces Marqueurs sont en relation étroite avec la Hiérarchie des Modèles de WordPress.

[Voir la liste complète de ces marqueurs dans le Codex officiel](https://codex.wordpress.org/fr:Marqueurs_conditionnels#Les_Conditions_Pour...)

## Actions
__[Source](https://wordpress.facemweb.com/actions-hooks/)__

### Introduction
Les actions sous WordPress répondent à la même logique que les niveaux d’exécution de Linux. Le meilleur système d’exploitation au monde (si si!) utilise une hiérarchisation de ses exécutions sur un nombre de niveaux prédéfinis (7 en général). Pour faire simple, disons qu’à son démarrage, Linux lance les services selon un ordre prédéfini, permettant ainsi un chargement coordonné et sans conflit du système.

Pour WordPress, c’est donc à peu près la même chose. Lors du chargement d’une page, le cœur du CMS exécute des tâches (les actions) selon une hiérarchie prédéterminée. Les actions ont en charge d’exécuter toutes les fonctions qui leur sont attribuées en fonction de leur ordre d’attribution, définie par l’argument d’ordonnance ou l’ordre d’apparition. On parle ainsi de Hooks (hameçon) pour désigner les niveaux d’exécution dans WordPress. En effet les actions viennent hameçonner les fonctions.

A travers les scripts d'éxécution est appellé la function ```do_action('nom_action')```.


### Exemple

Dans un fichier de ```function.php```

    // ma première action
    function dire_bonjour(){
        echo '<p class="hello"> Hello World !!</p>';
    }
    add_action( 'init', 'dire_bonjour');
    
### Exemple avec une notion d'ordre des hooks

    function dire_bonjour(){
        echo '<p class="hello"> Hello World !!</p>';
    }
    add_action( 'init', 'dire_bonjour');
    
    function dire_aurevoir(){
        echo '<p class="hello"> See ya World !!</p>';
    }
    add_action('wp','dire_aurevoir');
    
Le ```do_action('init')``` s'éxécute avant le ```do_action('wp')``` 

Voir la ressouce [Plugin_API](resources/Plugin_API.pdf)
