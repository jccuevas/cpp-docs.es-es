---
title: Información general de Funciones miembro
ms.date: 11/04/2016
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions [C++]
- inline functions [C++], treating member functions as
- member functions [C++], definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
ms.openlocfilehash: d1c3e069325363276e58a617d6ba21cb0b6e4ff0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188472"
---
# <a name="overview-of-member-functions"></a>Información general de Funciones miembro

Las funciones miembro son estáticas o no estáticas. El comportamiento de las funciones miembro estáticas difiere de otras funciones miembro porque las funciones miembro estáticas no tienen **ningún argumento implícito** . Las funciones miembro no estáticas tienen un puntero **this** . Las funciones miembro, ya sean estáticas o no estáticas, pueden definirse dentro o fuera de la declaración de clase.

Si una función miembro se define dentro de una declaración de clase, se trata como una función insertada y no es necesario calificar el nombre de función con su nombre de clase. Aunque las funciones definidas dentro de las declaraciones de clase ya se tratan como funciones insertadas, puede usar la palabra clave **inline** para documentar el código.

A continuación se muestra un ejemplo de declaración de una función dentro de una declaración de clase:

```cpp
// overview_of_member_functions1.cpp
class Account
{
public:
    // Declare the member function Deposit within the declaration
    //  of class Account.
    double Deposit( double HowMuch )
    {
        balance += HowMuch;
        return balance;
    }
private:
    double balance;
};

int main()
{
}
```

Si la definición de una función miembro está fuera de la declaración de clase, se trata como una función insertada solo si se declara explícitamente como **insertada**. Además, el nombre de función en la definición se debe calificar con su nombre de clase mediante el operador de resolución de ámbito (`::`).

El ejemplo siguiente es idéntico a la declaración anterior de clase `Account`, excepto en que la función `Deposit` se define fuera de la declaración de clase:

```cpp
// overview_of_member_functions2.cpp
class Account
{
public:
    // Declare the member function Deposit but do not define it.
    double Deposit( double HowMuch );
private:
    double balance;
};

inline double Account::Deposit( double HowMuch )
{
    balance += HowMuch;
    return balance;
}

int main()
{
}
```

> [!NOTE]
>  Aunque las funciones miembro pueden definirse dentro de una declaración de clase o por separado, las funciones miembro se pueden agregar a una clase una vez definida la clase.

Las clases que contienen funciones miembro pueden tener muchas declaraciones, pero las funciones miembro en sí deben tener solo una definición en un programa. Varias definiciones generan un mensaje de error en tiempo de vinculación. Si una clase contiene definiciones de funciones insertadas, las definiciones de función deben ser idénticas para observar esta regla de "una definición".
