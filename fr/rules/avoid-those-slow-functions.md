<!-- Performances -->
# Evitez Ces Fonctions Lentes

Il y a quelques fonctions PHP natives qui doivent être évitées pour des raisons de performances. Elles sont listées ci-dessous :

| Function | Alternative |
|---|---|
| array\_diff        | Utilisez array\_diff\_key, car les clés sont uniques |
| array\_intersect   | Utilisez array\_intersect\_key, car les clés sont uniques |
| array\_udiff       | Utilisez array\_diff\_key, car les clés sont uniques |
| array\_uintersect  | Utilisez array\_intersect\_key, car les clés sont uniques |
| array\_unique      | Utilisez array\_count\_values et array\_keys|
| uasort             | Construisez le tableau pour éviter les tris personnalisés (fonctions u\*sort) |
| uksort             | Construisez le tableau pour éviter les tris personnalisés (fonctions u\*sort) |
| usort              | Construisez le tableau pour éviter les tris personnalisés (fonctions u\*sort) |
| in\_array          | Construisez le tableau pour pouvoir utiliser isset() |
| preg\_replace      | Remplacez le par str\_replace(), pour les remplacements simples |
| array\_search      | Remplacez le par array\_key\_exists() |
| array\_shift       | Utilisez le tableau dans l'autre sens, avec array\_pop() |
| array\_unshift     | Utilisez le tableau dans l'autre sens, avec array\_push() |
| strstr             | Utilisez strpos() pour les recherches simples |
| uniqid()           | Toujours fournir le deuxième argument, l'entropie |
| array\_walk()      | Utilisez foreach($source as &$variable) { } |
| array\_map()       | Utilisez foreach($source as &$variable) { } |
| range()            | Vous pouvez utiliser les [generateurrs](http://php.net/manual/language.generators.overview.php), pour réduire la consommation de mémoire|

## Opérateur d'incrémentation

Même si ce n'est pas une fonction, l'opérateur de pré-incrémentation est plus rapide que celui de post-incrémentation, car ce dernier effectue une copie en mémoire.

Notez bien que remplacer `$i++` par `++$i` n'est pas inconditionnel : dans toutes les situations où la valeur initiale de post-incrémentation est assignée à une variable ou un argument doit être laissé tel quel.

```php
<?php

// Remplacements possibles
for($i = 0; $i < 10; $i++) { 
	//Some work here
}
$d++; // Seul sur sa ligne

// Une revue est nécessaire avant de faire le remplacement
$a = $b++;
$c = pow($d++, 2); // Élève $d à la puissance de 2, et non pas $d + 1

?>
```

## Détails De La Règle

Utilisez n'importe laquelle des fonctions ci-dessus produit une alerte.

<!--
### Options

-->

## Quand Ne Pas L'utiliser

Lorsque ces modifications sont des micro-optimisations en comparaison avec les optimizations d'architecture. Ne vous lancez pas dans un remplacement systématique, mais les utiliser du premier coup sera toujours bénéfique.

Lorsque vos conventions de codage vous poussent à utiliser l'une de ces fonctions plutôt que d'autres : il vaut mieux garder la convention cohérente.

## Bibliotgraphie

* [PHP Pitfalls](https://secure.phabricator.com/book/phabflavor/article/php_pitfalls/)
* [What's the difference between ++$i and $i++ in PHP?](http://stackoverflow.com/questions/1756015/whats-the-difference-between-i-and-i-in-php)
