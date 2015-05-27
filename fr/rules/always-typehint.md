<!-- Good Practices -->
# Utilisez Les Typehint

PHP autorise l'utilisation de `<nom de classe>`, `array` et `callable`, pour valider le type des données entrantes : les arguments doivent alors, respectivement, être un object de la classe  `<nom de classe>`, un tableau ou une fonction callback.

Lorsque c'est possible, les Typehint doivent être utilisés dans les signatures de méthodes ou de fonctions, afin d'assurer une validation simple des données en entrée. Les typehints sont réutilisés par PHP ainsi que par les outils d'analyze et les IDE pour valider les données, et, éventuellement, émettre des exceptions si les valeurs introduites ne sont pas du type escompté. 

Les Typehint peuvent être des classes ou bien des interfaces. 

Notons que PHP 7 va plus loin, et propose notamment des Typehint de retour, qui vérifie que la méthode retourne un type attendu. PHP 7 supporte aussi des types scalaires, tels que `integer` ou `string` et non plus seulement des types objets. 

Il est recommandé d'utiliser les Typehint autant que possible.

## Détails de la règle

Cette règle fait la promotion des Typhehint.

Les exemples suivants sont des erreurs : 

```php
<?php

function foo($a) {
	// $a devrait être un objet, d'une classe qui, elle ou un de ses parents, dispose d'une méthode appelée `methodeAppelee`
	$a->methodeAppelee();
}
?>
```

Les exemples suivants sont ambigus, et ne devraient pas générer d'alerte : 

```php
<?php

function foo($a) {
	$b = $a . '1'; // $a peut être une string ou bien un objet qui dispose de la méthode __toString()
}

function bar($a, $b) {
	$c = $a + 1; // $a pourrait être un nombre ou un tableau
}
?>
```

Les exemples suivants ne sont pas des erreurs : 

```php
<?php

function foo($a) {
	$b = $a + 1; // $a pourrait être un entier
	$c = $a * 1.2; // $a pourrait etre un nombre décimal
}

?>
```

<!--
### Options

## When Not To Use It

## Further Readings
-->

