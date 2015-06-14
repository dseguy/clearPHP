<!-- Performances -->
# Utilisez Les Assignations Courtes

Certains opérateurs disposent d'une version "Effectue et assigne", qui ressemble à une version compacte de l'assignation avec l'opérateur. Par exemple : 

```php
<?php
$x = $x + 2;
// peut être écrit
$x += 2;
?>
```

Cette approche est la meilleure pour la lisibilité : elle rend évidente l'incrémentation de la variable. C'est typiquement le cas lorsque cette variable est utilisée pour collecter des données jusqu'à ce que la variable soit finalement utilisée, comme une concaténation de code HTML.

Les assignations courtes sont plus efficaces en terme de mémoire. Elles évitent une copie de données en mémoire, en plus d'une allocation. Cela peut aussi entraîner un gain de performances, si ces assignations sont utilisées intensivement. 

Il est recommandé de toujours utiliser les assignations courtes.

## Détails De La Règle

Cette règle cible les assignations qui peuvent être raccourcies.

Les assignations courtes sont les suivantes :
* +=
* -=
* *=
* /=
* %=
* **=
* .=
* &=
* |=
* ^=
* >>=
* <<=

Les exemples suivants sont considérés comme érronés : 

```php
<?php

// + et * sont commutables
$a = $a + $b;
$a = $b + $a;

// les autres opérateurs ne peuvent être commutés : seule cette version peut être remplacée par une assignation courte
$a = $a - $b;

// Peut être raccourci 
$a = $a . $b . $c; 

?>
```

Les exemples suivants sont valides :

```php
<?php

// certains opérateurs ne peuvent être commutés
$a = $b - $a; 

?>
```
<!--
## When Not To Use It
If the project doesn't use any OOP feature, it may ignore this rule.


## Further Reading

-->