<!-- Good Practices -->
# Pas d'Exit

Il est possible d'interrompre l'exécution d'un script avec les commandes `die` et `exit`. Elles stoppent l'exécution et détruisent immédiatement toutes les ressources.

```php
<?php

if (mysql_connect('localhost', 'user', 'pass')) {
	die('Pas de base de données');
}

?>
```

Interrompre une application avec `die` or `exit` fonctionne aussi dans une bibliothèque. Cela rend la localisation de l'interruption très difficile, notamment lorsque ces commandes sont utilisées sans aucun arguments, et qu'elles ne donnent aucune indication sur la localisation ou la raison du problème. 

Cela empêche aussi le programme principal de tenter un sauvetage ou de clore proprement les ressources : ces dernières sont détruites en l'état, au moment du die. 

Il est recommandé d'utiliser `throw` pour lancer une exception ou d'émettre une erreur PHP (avec `trigger_error`), ou encore d'utiliser le mécanisme de gestion d'erreur disponible dans votre application (retourner un code d'erreur, appeler une méthode `erreur`, etc..). 

## Détails De La Règle

La règle cible toutes les utilisations de `die` or `exit`. 

```php
<?php

exit();
die(__METHOD__);

?>
```
Cette règle s'applique aussi aux bibliothèques bâties sur le concept de débugage avec `var_dump`, telles que [Kint](http://raveren.github.io/kint/) ou [Krumo](http://krumo.sourceforge.net/), ou d'autres encore (liste non-exhaustive). Ces bibiothèques disposent de directives de configuration qui permettent de contrôler l'affichage ou non des erreurs, contrairement aux fonctions natives telles que `print_r` et `var_dump`. Même si c'est indéniablement mieux, il est préférable d'éviter la possibilité d'interrompre l'exécution. 


## Quand L'Éviter
Lorsque le code est exécuté en ligne de commande, `exit` et `die` permettent de conclure le script et de retourner un statut, tout comme `return`. 

## Bibliographie

* [Exceptions](http://php.net/manual/en/language.exceptions.php)
* [Trigger_error](http://php.net/manual/en/function.trigger-error.php)
* [Return](http://php.net/manual/en/function.return.php)