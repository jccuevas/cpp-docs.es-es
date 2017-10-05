---
title: "Información general de las funciones miembro | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- this pointer, and nonstatic member functions
- nonstatic member functions
- inline functions, treating member functions as
- member functions, definition in class declaration
ms.assetid: 9f77a438-500e-40bb-a6c6-544678f3f4c8
caps.latest.revision: 6
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: cc73317962c92a7f35d103b342ca52aa0bef4f2e
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="overview-of-member-functions"></a>Información general de Funciones miembro
Las funciones miembro son estáticas o no estáticas. El comportamiento de las funciones miembro estáticas difiere de otras funciones miembro porque las funciones miembro estáticas no tienen implícita no **esto** argumento. Funciones miembro no estáticas tienen un **esto** puntero. Las funciones miembro, ya sean estáticas o no estáticas, pueden definirse dentro o fuera de la declaración de clase.  
  
 Si una función miembro se define dentro de una declaración de clase, se trata como una función insertada y no es necesario calificar el nombre de función con su nombre de clase. Aunque las funciones definidas dentro de declaraciones de clase ya se tratan como funciones insertadas, puede usar el **en línea** palabra clave para documentar el código.  
  
 A continuación se muestra un ejemplo de declaración de una función dentro de una declaración de clase:  
  
```  
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
  
 Si la definición de la función de miembro está fuera de la declaración de clase, se trata como una función insertada solo si se declara explícitamente como **en línea**. Además, el nombre de función en la definición se debe calificar con su nombre de clase mediante el operador de resolución de ámbito (`::`).  
  
 El ejemplo siguiente es idéntico a la declaración anterior de clase `Account`, excepto en que la función `Deposit` se define fuera de la declaración de clase:  
  
```  
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
  

