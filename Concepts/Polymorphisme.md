# 🔄 Polymorphisme en C# / .NET

## 📑 Sommaire
<!-- TOC -->
- [📘 Définition](#-définition)
- [🎯 Objectifs du polymorphisme](#-objectifs-du-polymorphisme)
- [🧠 Comprendre simplement](#-comprendre-simplement)
- [📦 Polymorphisme vs Héritage](#-polymorphisme-vs-héritage)
- [🧪 Exemple concret en C#](#-exemple-concret-en-c)
- [✅ Utilisation](#-utilisation)
- [📚 Ressources](#-ressources)
<!-- /TOC -->

---

## 📘 Définition

Le **polymorphisme** (du grec “plusieurs formes”) est un principe de la programmation orientée objet qui permet :

> D’utiliser **le même nom de méthode** sur des objets différents,  
> et que **chacun exécute son propre comportement** selon son type réel.

En C#, cela passe par l’utilisation des mots-clés `virtual` (dans la classe de base) et `override` (dans la classe dérivée).

---

## 🎯 Objectifs du polymorphisme

- 📦 Réutiliser du code via des classes de base.
- 🔁 Exécuter des comportements différents **à partir du même appel**.
- 🧩 Écrire du code plus générique et extensible.
- ✅ Respecter le **principe de substitution de Liskov** (L du SOLID).

---

## 🧠 Comprendre simplement

Imagine un **bouton "Allumer"**.

Tu le donnes à :
- une **télé** → elle s’allume,
- une **radio** → elle joue de la musique,
- un **ventilateur** → il se met à tourner.

➡️ Même action (`Allumer()`), mais **chaque appareil réagit à sa façon**.

C’est **exactement** ce que permet le polymorphisme :  
> Tu appelles une méthode sur une variable d’un type parent, et **le bon comportement est exécuté selon le vrai type de l’objet.**

---

## 📦 Polymorphisme vs Héritage

| 🧬 Héritage                            | 🔄 Polymorphisme                                         |
|--------------------------------------|----------------------------------------------------------|
| Permet à une classe de **réutiliser** le code d’une autre | Permet à une méthode d’**avoir plusieurs comportements** |
| Définit une relation "est un"        | Utilise des méthodes `virtual` / `override`             |
| Exemple : `Chien : Animal`           | Exemple : `animal.Parler()` → exécute Chien ou Chat     |
| Ne change pas le comportement        | Change dynamiquement le comportement à l'exécution       |
| Pas besoin de `virtual` ou `override` | Requiert `virtual` dans la base et `override` dans la dérivée |

---

## 🧪 Exemple concret en C#

```csharp
public class Animal
{
    public virtual void Parler()
    {
        Console.WriteLine("L’animal fait un bruit");
    }
}

public class Chien : Animal
{
    public override void Parler()
    {
        Console.WriteLine("Le chien aboie");
    }
}

public class Chat : Animal
{
    public override void Parler()
    {
        Console.WriteLine("Le chat miaule");
    }
}

```

## ✅ Utilisation

```csharp
List<Animal> animaux = new List<Animal>
{
    new Chien(),
    new Chat()
};

foreach (var animal in animaux)
{
    animal.Parler(); // Appelle la bonne méthode selon le vrai type
}
// Donc ici le chien aboie et le chat miaule

```

## 📚 Ressources

- [Documentation Microsoft - Polymorphisme](https://learn.microsoft.com/fr-fr/dotnet/csharp/fundamentals/object-oriented/polymorphism?utm_source=chatgpt.com)