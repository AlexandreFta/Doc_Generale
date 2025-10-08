# 🛡️ Abstraction en C# / .NET

## 📑 Sommaire
<!-- TOC -->
- [📘 Définition](#-définition)
- [🎯 Objectifs de l'abstraction](#-objectifs-de-labstraction)
- [⚙️ Classes abstraites & Interfaces](#-classes-abstraites--interfaces)
- [🧪 Exemple concret en C#](#-exemple-concret-en-c)
- [📚 Ressources](#-ressources)
<!-- /TOC -->

---

## 📘 Définition

L'**abstraction** est un principe de la POO qui consiste à **cacher les détails d’implémentation** et à **exposer uniquement les fonctionnalités essentielles**.  

L’idée est que tu vois *ce que l’objet fait*, pas *comment il le fait*. Cela permet de simplifier l’utilisation des classes, de rendre le code plus lisible, et de séparer "contrat" vs "implémentation".

---

## 🎯 Objectifs de l'abstraction

- Réduire la complexité en ne montrant que ce qui est nécessaire.  
- Promouvoir la séparation des responsabilités (contrat vs implémentation).  
- Rendre le code plus flexible : on peut changer l’implémentation sans toucher à ce qui dépend de l’abstraction.  
- Faciliter le test : on peut simuler l’abstraction dans les tests (interfaces/classes abstraites).

---

## ⚙️ Classes abstraites & Interfaces

- Une **classe abstraite** (`abstract class`) peut contenir des méthodes **implémentées** et des méthodes **abstraites** (sans corps). :contentReference[oaicite:0]{index=0}  
- Elle ne peut pas être instanciée directement. :contentReference[oaicite:1]{index=1}  
- Une **interface** est un contrat pur : elle définit des méthodes ou propriétés que les classes qui l’implémentent doivent fournir.  
- Tu choisis une interface si tu veux juste définir un contrat. Tu choisis une classe abstraite si tu veux fournir du comportement par défaut **et** forcer certaines parties à être définies dans la classe dérivée.  
- Le modificateur `abstract` ne peut pas être combiné avec `sealed`, car `sealed` empêche l’héritage, tandis que `abstract` le requiert. :contentReference[oaicite:2]{index=2}  

---

## 🧪 Exemple concret en C#

```csharp
// Définition de l'abstraction via une classe abstraite
public abstract class Animal
{
    public string Name { get; set; }

    public Animal(string name)
    {
        Name = name;
    }

    // Méthode abstraite : chaque classe dérivée doit l’implémenter
    public abstract void MakeSound();

    // Méthode concrète : comportement partagé par tous les dérivés
    public void Eat()
    {
        Console.WriteLine($"{Name} mange.");
    }
}

// Classe dérivée concrète
public class Dog : Animal
{
    public Dog(string name) : base(name) { }

    public override void MakeSound()
    {
        Console.WriteLine($"{Name} aboie : Ouaf !");
    }
}

```

## 📚 Ressources

- [Documentation Microsoft - Abstraction](https://learn.microsoft.com/fr-fr/dotnet/csharp/language-reference/keywords/abstract?utm_source=chatgpt.com)
- [Documentation Microsoft - Abstraction Types et Interfaces](https://learn.microsoft.com/en-us/dotnet/standard/design-guidelines/abstractions-abstract-types-and-interfaces?utm_source=chatgpt.com)


