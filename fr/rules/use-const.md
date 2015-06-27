<!-- Good Practices -->
# Utilisez Const

Il y a deux moyens de créer des constantes en PHP : `const` et `define`. 

`const` sert aussi à créer des constantes, et pas seulement des constantes de classe. Ces constantes sont alors placées dans l'espace de nom courant. Depuis PHP 5.6, les expressions statiques peuvent être utilisées lors de la création de ces constantes, ce qui donne une importante flexibilité. Lorsqu'il n'est pas utilisé dans une classe, `const` doit être placé dans la racine de l'espace de noms : il ne peut être dans une fonction, dans une instruction `if..then` ou dans une boucle. En fait, tout cela permet de définir la valeur de la constante dès la compilation. Cela confère à `const` ses avantages : il est légèrement plus rapide  et plus lisible que son cousin, `define`. 

`define`, d'un autre coté, est la fonction traditionelle pour créer les constantes en PHP. Il peut être utilisé n'importe où dans le code, et même avec des expressions dynamiques. Les résultat est une constante de l'espace global, ou bien d'un espace de nom si ce dernier a été inclut dans le nom de la constante lors de la définition. Ces constantes peuvent être rendues insensibles à la casse.

`define` s'avère un peu plus lent que `const`, et ne profite pas des systèmes d'opcode. Cela est d'autant plus vrai que le nombre de constantes est de l'application est grand.

Il est recommandé d'utiliser `const` dès que c'est possible.

## Détails De La Règle

L'exemple suivant n'est pas valide : 

```php
<?php

define('a', 1);
define('b', 'a' . 'c');
define('c', uneClasse::constante);

?>
```

L'exemple suivant est correct : 

```php
<?php

define('l', 3, true);
define('m', $x, true);
define('n', array(1,2,3), true); // avant PHP 5.6

?>
```

## Quand L'Éviter
* Pour la compatibilité ascendante
* Pour charger des directives de configuration sous forme de constante, `define()` est toujours plus pratique. 

## Bibliographie

* [define() versus const (PHP Best practises)](https://phpbestpractices.org/#constants)
* [define vs const (Stackoverflow)](http://stackoverflow.com/questions/2447791/define-vs-const)

