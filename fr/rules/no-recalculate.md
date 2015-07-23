<!-- Performances -->
# Pas De Recalculs

Dans une méthode, il est toujours plus rapide de mettre en cache une valeur que de la recalculer. Par exemple, 

```php
<?php

    $htmlLink = '<a href="'.strtr(strtolower($url), ' ', '-').'.php"><img src="'.strtr(strtolower($url), ' ', '-').'.png" alt="$title"></a>';
?>
```

Dans cet exemple, les URI du lien et de l'image sont construits à partir de la variable `$title`, afin de protéger les caractères spéciaux. Appeler les fonctions `strtr` et `strtolower`, ou simplement l'une des deux, sera toujours plus lent que de mettre le résultat en cache dans une variable.

```php
<?php

	$baseUri = strtr(strtolower($url), ' ', '-');
    $htmlLink = '<a href="'.$baseUri.'.php"><img src="'.$baseUri.'.png" alt="$title"></a>';

?>
```

Ce nouveau code présente l'avantage supplémentaire d'être plus facile à lire, et à modifier (tant que les deux URI sont les mêmes).

Lorsqu'un appel de fonction est utilisé seulement une fois, il n'y a pas d'avantage à le mettre en variable. Dès que cet appel est fait deux fois, la mise en cache est plus rapide. Evidemment, plus la fonction est complexe, plus le gain est important. Notamment, la mise en cache d'appels de fonctions utilisateurs est bien plus recommandé que la mise en cache de fonctions natives.

Il est recommandé d'éviter les recalculs dans une méthode. Au niveau global, il est toutefois recommandé de les éviter car les recalculs sont difficiles à identifier.

## Détails De La Règle

Cette règle cible les appels multiples aux mêmes fonctions, avec les mêmes valeurs.

Les exemples suivants sont à éviter : 

```php
<?php

	// $url est calculé deux fois de la même manière
    $htmlLink = '<a href="'.strtr(strtolower($url), ' ', '-').'.php"><img src="'.strtr(strtolower($url), ' ', '-').'.png" alt="$title"></a>';

?>
```

Les exemples suivants sont valides : 

```php
<?php

	// les URI sont distinctes
    $htmlLink = '<a href="'.strtr(strtolower($url), ' ', '-').'.php"><img src="'.strtr(strtolower($url.'?id='.time()), ' ', '-').'.png" alt="$title"></a>';
    
    // les appels de la fonction sont différents
    $a = foo(1);
    $b = foo(2);
?>
```
<!--

### Options
-->

## Quand L'Éviter
* Évitez de créer des variables de cache au niveau global, car elles sont difficiles à identifier et à réutiliser au niveau de l'ensemble de l'application. Il est plus sécuritaire de le faire à l'intérieur d'une méthode.
* Certains appels de méthodes effectuent des calculs mais modifient aussi l'état d'un systène, comme par exemple `ini_set` ou une méthode de changement d'état dans une classe. Si les résultats peuvent être mis en cache, l'appel reste nécessaire.

<!--
## Further Readings
-->

