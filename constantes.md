# Constantes

Nous le savons, `define()` et ` const` sont utilisés pour déclarer des constantes dans un script PHP.

Syntaxe

```php
<?php
   const FOO = 'bar';
   define('FOO', 'bar') ;
?>
```

La différence fondamentale entre ces deux manières est que `const` définit les constantes au moment de la compilation, alors que `define()` les définit au moment de l’exécution. 

Du coup, nous ne pouvons pas utiliser le mot-clé `const` pour déclarer des constantes dans des blocs conditionnels, étant donné que ceux-ci sont évalués lors de l’exécution. Avec `define()` nous pouvons le faire.
    

```php
<?php
  if(bool){
      const FOO = 'bar' ; // invalide
  }
  if(bool){
    define('FOO', 'bar') ; //valide
  }
?>
```
Une autre conséquence liée au moment de la définition de la constante est que `const` accepte un scalaire statique (nombre, chaîne de caractères ou autres constantes comme `true`, `false`, `null`, `__FILE__`, etc. ), alors que `define()` prend n’importe quelle expression.

Les constantes définies avec `const` sont toujours sensibles à la casse, alors que `define()` vous permet de contrôle cet aspect grâce à son troisième argument, booléen.

`const` peut être utilisé au sein d’une classe ou d’une interface pour déclarer une constante de classe ou une constante d’interface, alors que `define()` ne peut pas être utilisé pour cette raison.
    

```php
<?php
class Abc{
	const FOO = 'bar' ; // Valide
  public static function getFoo()
  {
    return self::FOO; // Valide
  }	
}

// mais

class Abc{
	define('FOO', 'bar') ; // Invalide
	public static function getFoo()
  {
    return self::FOO; // Invalide
  }
}
?>
```

L’exemple ci-dessus montre que nous pouvons déclarer une constante à l’intérieur d’une classe avec le mot-clé `const` mais que `define()` ne peut pas être utilisé pour déclarer une constante à l’intérieur d’une classe.