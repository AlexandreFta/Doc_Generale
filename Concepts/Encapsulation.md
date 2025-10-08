# 🔐 Encapsulation en C# / .NET

## 📑 Sommaire
<!-- TOC -->
- [📘 Définition](#-définition)
- [🎯 Objectifs de l'encapsulation](#-objectifs-de-lencapsulation)
- [📦 Encapsulation dans les projets .NET](#-encapsulation-dans-les-projets-net)
- [🧪 Exemple concret en C#](#-exemple-concret-en-c)
- [📚 Ressources](#-ressources)
<!-- /TOC -->

---

## 📘 Définition

L'**encapsulation** est un des piliers de la programmation orientée objet (POO).  
Elle consiste à **cacher les détails internes d’une classe** et à **exposer uniquement une interface contrôlée** pour accéder et modifier ses données.  

En C#, cela se réalise via les **modificateurs d'accès** (`private`, `public`, `protected`, `internal`) et les **propriétés** (`get`, `set`).  

Le but est de **protéger l'état interne de l'objet** contre des modifications non contrôlées et d'assurer la cohérence des données.

---

## 🎯 Objectifs de l'encapsulation

- 🔒 **Protéger les données internes** d'une classe contre un accès direct inapproprié.  
- ⚙️ **Masquer la complexité** de l'implémentation interne.  
- 🔄 **Contrôler comment les données sont modifiées** via des règles métier dans les accesseurs.  
- 🛠️ Faciliter la maintenance et l'évolution du code en isolant les changements.

---

## 📦 Encapsulation dans les projets .NET

- DTOs (Data Transfer Objects) : encapsulent les données échangées entre couches ou services.
- ViewModels dans les applications MVVM : encapsulent l’état de l’interface utilisateur.
- Services : encapsulent la logique métier et les appels aux bases de données ou APIs.

---

## 🧪 Exemple concret en C#

```csharp
public class BankAccount
{
    // Champ privé (encapsulé)
    private decimal _balance;

    // Propriété en lecture seule pour accéder au solde
    public decimal Balance => _balance;

    // Méthode pour déposer de l'argent
    public void Deposit(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Le montant doit être positif", nameof(amount));
        
        _balance += amount;
    }

    // Méthode pour retirer de l'argent
    public void Withdraw(decimal amount)
    {
        if (amount <= 0)
            throw new ArgumentException("Le montant doit être positif", nameof(amount));
        if (amount > _balance)
            throw new InvalidOperationException("Fonds insuffisants");

        _balance -= amount;
    }
}

```

---

## 📚 Ressources

- [Documentation Microsoft - Les Propriétés](https://learn.microsoft.com/fr-fr/dotnet/csharp/programming-guide/classes-and-structs/properties)
- [Documentation Microsoft - Les Modificateurs d'accès](https://learn.microsoft.com/fr-fr/dotnet/csharp/programming-guide/classes-and-structs/access-modifiers)
- [Documentation Geeksforgeeks - Encapsulation](https://www.geeksforgeeks.org/c-sharp/encapsulation-in-c-sharp/)
- [Documentation C# Corner - Encapsulation](https://www.c-sharpcorner.com/article/encapsulation-in-C-Sharp/)

