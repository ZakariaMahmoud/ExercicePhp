# Exercices corrigés en Langage PHP 
>**Exercice 1 :**
>Parmi les variables suivantes, les quelles ont un nom valide : mavar, $mavar, $var5, $_mavar, $_5var, $__élément1, $hotel4* ?

Les noms $mavar, $var5, $_mavar, $_5var, $__élément1 respectent les conventions. Les autres ne sont pas valides.
>**Exercice 2 :**
>Donnez les valeurs de $x, $y, $z à la fin du script suivant :
``````php
<?php
$x="PostgreSQL";
$y="MySQL";
$z=$x;
$x="PHP 5";
$y=$x;

echo " x = $x <br>" ;// x= PHP 5
echo " y = $y <br>" ;// y= PHP 5
echo " z = $z <br>" ; // z= PostgreSQL
?>
``````
> **Exercice 3 :**
> Lisez les valeurs des variables du script de l’exercice 2 à l’aide du tableau $GLOBALS.

``````php
<?php
$x="PostgreSQL";
$y="MySQL";
$z=$x;
$x="PHP 5";
$y=$x;

echo " x = ".$GLOBALS['x']." <br>" ;// x= PHP 5
echo " y = ".$GLOBALS['y']." <br>" ;// y= PHP 5
echo " z = ".$GLOBALS['z']." <br>"; // z= PostgreSQL
?>
``````
> **Exercice 4 :**
> Déterminez le numéro de version de PHP, le nom du système d’exploitation de votre serveur ainsi que la langue du navigateur du poste client.

``````php
<?php
echo "Version de PHP : ",PHP_VERSION, "<br>";

echo "Système d'exploitation du serveur : ",PHP_OS, "<br>";

echo "Langue du navigateur client :",$_SERVER["HTTP_ACCEPT_LANGUAGE"], "<br>";
?>
``````
> **Exercice 5 :**
> Donner la valeur de chacune des variables pendant et à la fin du script suivant et vérifier l’évolution du type de ces variables :
``````php
<?php
$x="PHP5";
var_dump($x);
$a[]=&$x;
var_dump($a);
$y=" 5 eme version de PHP";
var_dump($y);
$z=$y*10;
var_dump($z);
$x.=$y;
var_dump($x);
$y*=$z;
var_dump($y);
$a[0]="MySQL";
var_dump($a[0]);
?>
``````

> **Exercice 6 :**
> Donnez la valeur des variables $x, $y, $z à la fin du script : 
> $x="7 personnes"; 
> $y=(integer) $x; 
> $x="9E3";
> $z=(double) $x;

``````php
<?php
$x="7 personnes"; 
var_dump($x); // string(11) "7 personnes"
echo "<br>";
$y=(integer)$x; 
var_dump($y);// int(7)
echo "<br>";
$x="9E3";
var_dump($x);//string(3) "9E3"
echo "<br>";
$z=(double)$x;
var_dump($z); //int (9000) parce que 9e3= 9 x 10^3
?>
``````

> **Exercice 7 :**
>
> Donnez la valeur booléenne des variables $a, $b, $c, $d, $e et $f : 
>
> $a="0"; $b="TRUE"; $c=FALSE; $d=($a OR $b); $e=($a AND $c); $f=($a XOR $b)

```php
<?php
$a="0";
var_dump($a); // string(1) "0"
echo "<br>";
$b="TRUE";
var_dump($b); // string(4) "TRUE"
echo "<br>";
$c=FALSE;
var_dump($c); // bool(false)
echo "<br>";
$d=($a OR $b);
var_dump($d); // bool(true)
echo "<br>";
$e=($a AND $c);
var_dump($e);// bool(false)
echo "<br>";
$f=($a XOR $b);
var_dump($f);// bool(true)
echo "<br>";
?>
```

> **Exercice 8 :**
>
> Rédigez une expression conditionnelle pour tester si un nombre est à la fois un multiple de 3 et de 5.

```php
<?php
$nombre=15;
if($nombre%3==0 && $nombre%5==0)
	echo "Le nombre $nombre est multiple de 3 et 5.";
else 
	echo "Le nombre $nombre n'a pas multiple de 3 et 5.";
?>
```

> **Exercice 9 :**
>
> Écrivez une expression conditionnelle utilisant les variables $age et $sexe dans une instruction if pour sélectionner une personne de sexe féminin dont l’âge est compris entre 21 et 40 ans et afficher un message de bienvenue approprié.

```php
<?php
$age=25;
$sexe="feminin";

if ($age>=20 && $age<=40 AND $sexe=="feminin")
	echo "Bianvenu  Madame."; 
?>
```

> **Exercice 10 :**
>
> Effectuez une suite de tirages de nombres aléatoires jusqu’à obtenir une suite composée d’un nombre pair suivi de deux nombres impairs.

```php
<?php
 do{
     $pair=rand(1,100);
     $impair1=rand(1,100);   
     $impair2=rand(1,100);
	echo "  [$pair,$impair1,$impair2] ";
 }while($pair%2!=0 || $impair1%2!=1 || $impair2%2!=1);  
?>
```

> **Exercice 11 :**
>
> Choisissez un nombre de trois chiffres. Effectuez ensuite des tirages aléatoires, et comptez le nombre de tirages nécessaire pour obtenir le nombre initial. Arrêtez les tirages, et affichez le nombre de coups réalisés. Réalisez ce script d’abord avec l’instruction while puis avec l’instruction for.

```php
<?php
    /** Boucle While **/
$numbre=567;
$randNumbre=0;
$coups=0;
while($randNumbre!=$numbre){

    $randNumbre=rand(100,999);
    echo "--[ $randNumbre ]";
    $coups++;
}
echo "<br>Le nombre de coups est : $coups";
?>
```
```php
<?php
 /** Boucle For **/
$numbre=567;
$randNumbre=0;
$coups;
for($coups=0;$randNumbre!=$numbre;$coups++){ 
    $randNumbre=rand(100,999);
    echo "--[ $randNumbre ]";
    $coups++;
}
echo "<br>Le nombre de coups est : $coups";
?>
```
> **Exercice 12 :**
>
> Créez un tableau dont les indices varient de 11 à 36 et dont les valeurs sont des lettres de A à Z. Lisez ensuite ce tableau avec une boucle for puis une boucle foreach, et affichez les indices et les valeurs (la fonction chr(n) retourne le caractère dont le code ASCII vaut n).

```php
<?php
for ($i = 11; $i <= 36; $i++) {
    $tab[$i] = chr(54 + $i);
}
//Lecture avec for
for ($i = 11; $i <= 36; $i++) {
    echo "Elément d'indice $i : $tab[$i] <br>";
}
echo "<hr />";
//Lecture avec foreach
foreach ($tab as $key => $value) {
    echo "Elément d'indice $key : $value <br>";
}
?>
```

> **Exercice 13 :**
>
> Utilisez une boucle while pour déterminer le premier entier obtenu par tirage aléatoire qui soit un multiple d’un nombre donné. Écrivez la variante utilisant la boucle do...while.

```php
<?php
$nombre = 18;
$x = rand(0, 1000);
//Boucle while
while ($x % $nombre != 0) {
    $x = rand(0, 1000);
}
echo "$x est multiple de $nombre";
?>
```

```php
<?php
$nombre = 18;
//Boucle do...while
do {
    $x = rand(0, 1000);
} while ($x % $nombre != 0);
echo "$x est multiple de $nombre";
?>
```

> **Exercice 14 :**
>
> Recherchez le PGCD (plus grand commun diviseur) de deux nombres donnés. Gérez au moyen d’une exception le cas où au moins un des nombres n’est pas entier.

```php
<?php
//Il faut $A > $B
$A = 9876;
$B = 5432;
try {
    if (!(is_integer($A) or is_integer($b))) {
        throw new Exception("Nombre(s) non entiers !");
    } else {
        echo "Le PGCD de $A et $B est : ";
        do {
            $R = $A % $B;
            $A = $B;
            $B = $R;
        } while ($R != 0);
        echo $A;
    }
} catch (Exception $except) {
    echo $except->getMessage();
}
?>
```

----

---

**Réaliser Par : Mahmoud Zakaria.**

* **Github** : [ZakariaMahmoud](https://github.com/ZakariaMahmoud/)

* **Email** : zakaria.forwork@gmail.com
* **Linkdin** : [zakariamahmoud](https://www.linkedin.com/in/zakariamahmoud/)