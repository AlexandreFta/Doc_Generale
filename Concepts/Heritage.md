# 🧬 Héritage en C# / .NET

## 📑 Sommaire
<!-- TOC -->
- [📘 Définition](#-définition)
- [🎯 Objectifs de l'héritage](#-objectifs-de-lhéritage)
- [🧰 Syntaxe de base en C#](#-syntaxe-de-base-en-c)
- [⚙️ Gestion de l'héritage avec les mots-clés](#️-gestion-de-lhéritage-avec-les-mots-clés)
- [🧪 Exemple concret en C#](#-exemple-concret-en-c)
- [📚 Ressources](#-ressources)
<!-- /TOC -->

---

## 📘 Définition

L’**héritage** est un principe fondamental de la programmation orientée objet (POO).  
Il permet à une **classe dérivée** d’hériter des membres (méthodes, propriétés, champs) d’une **classe de base**. Cela facilite la réutilisation du code et permet de créer des relations hiérarchiques entre types.

---

## 🎯 Objectifs de l'héritage

- 🔁 Réutiliser du code existant sans duplication.  
- 🧩 Modéliser des relations de type « est-un » (`is-a`).  
- 🧱 Favoriser une architecture claire avec des comportements partagés.  
- 🎯 Permettre la spécialisation de certaines fonctionnalités.

---

## 🧰 Syntaxe de base en C#

```csharp
// Classe de base
public class Animal
{
    public void Move()
    {
        Console.WriteLine("L'animal se déplace");
    }
}

// Classe dérivée
public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine("Le chien aboie");
    }
}

```

---

## ⚙️ Gestion de l'héritage avec les mots-clés

- class ➡️ Permet de définir une classe, qui peut être une base (parent) ou dérivée (enfant).
- : ➡️ Sert à hériter d'une classe ou à implémenter une interface. Ex : class Fille : Mère
- base ➡️ Permet d'accéder à la classe parente (constructeur ou méthode).

```csharp

class Animal {
    public Animal() {
        Console.WriteLine("Animal créé.");
    }
}

class Chien : Animal {
    public Chien() : base() {
        Console.WriteLine("Chien créé.");
    }
// Le mot base() appelle le constructeur de Animal avant d’exécuter celui de Chien.
}

```

- virtual ➡️ Marque une méthode dans la classe de base comme surchargeable.
- override ➡️ Utilisé dans la classe dérivée pour remplacer une méthode marquée virtual.

```csharp

class Animal {
    public Animal() {
        Console.WriteLine("Animal créé.");
    }
}

class Chien : Animal {
    public Chien() : base() {
        Console.WriteLine("Chien créé.");
    }
// Parler() est modifiable dans les classes enfants grâce à virtual.
//Chien remplace le comportement avec override.
}

```

- new ➡️ Créer une nouvelle méthode avec le même nom, mais indépendante de celle du parent.
- abstract ➡️ Indique qu'une classe ou méthode est incomplète et doit être héritée/surchargée.

```csharp

abstract class Animal {
    public abstract void Parler();
}

class Chien : Animal {
    public override void Parler() {
        Console.WriteLine("Le chien aboie.");
    }
// Animal est abstrait : il ne peut pas être instancié directement.
//Chien doit implémenter Parler().
}

```

- sealed ➡️ Empêche une classe d’être héritée. Peut aussi bloquer la surcharge d’une méthode.
- protected ➡️ Rend un membre accessible aux classes dérivées, mais pas à l’extérieur.

---

## 🧪 Exemple concret en C#

```csharp

public class Animal
{
    public string Name { get; set; }

    public void Move()
    {
        Console.WriteLine($"{Name} se déplace");
    }
}

public class Dog : Animal
{
    public void Bark()
    {
        Console.WriteLine($"{Name} aboie : Ouaf !");
    }
}

// Utilisation
var dog = new Dog();
dog.Name = "Rex";
dog.Move();   // Hérité de Animal
dog.Bark();   // Propre à Dog

```

---

## 📚 Ressources

- [Documentation Microsoft - Héritage types](https://learn.microsoft.com/fr-fr/dotnet/csharp/fundamentals/object-oriented/inheritance)
- [Documentation Microsoft - Héritage](https://learn.microsoft.com/fr-fr/dotnet/csharp/fundamentals/tutorials/inheritance?utm_source=chatgpt.com)
- [Documentation Microsoft - Mot Clés](https://learn.microsoft.com/fr-fr/dotnet/csharp/programming-guide/classes-and-structs/versioning-with-the-override-and-new-keywords)
- [Documentation Microsoft - Sealed](https://learn.microsoft.com/fr-fr/dotnet/csharp/language-reference/keywords/sealed)