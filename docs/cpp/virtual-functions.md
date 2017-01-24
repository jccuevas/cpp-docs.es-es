---
title: "Funciones virtuales | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases derivadas, funciones virtuales"
  - "funciones [C++], funciones virtuales"
  - "funciones virtuales"
ms.assetid: b3e1ed88-2a90-4af8-960a-16f47deb3452
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Funciones virtuales
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Una función virtual es una función miembro que se espera volver a definir en clases derivadas.  Cuando se hace referencia a un objeto de clase derivada mediante un puntero o una referencia a la clase base, se puede llamar a una función virtual para ese objeto y ejecutar la versión de la clase derivada de la función.  
  
 Las funciones virtuales garantizan que se llame a la función correcta para un objeto, con independencia de la expresión utilizada para llamarla.  
  
 Suponga que una clase base contiene una función declarada como [virtual](../cpp/virtual-cpp.md) y una clase derivada define la misma función.  La función de la clase derivada se invoca para los objetos de la clase derivada, aunque se llame mediante un puntero o una referencia a la clase base.  En el ejemplo siguiente se muestra una clase base que proporciona una implementación de la función `PrintBalance` y dos clases derivadas  
  
```  
// deriv_VirtualFunctions.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Account {  
public:  
   Account( double d ) { _balance = d; }  
   virtual double GetBalance() { return _balance; }  
   virtual void PrintBalance() { cerr << "Error. Balance not available for base type." << endl; }  
private:  
    double _balance;  
};  
  
class CheckingAccount : public Account {  
public:  
   CheckingAccount(double d) : Account(d) {}  
   void PrintBalance() { cout << "Checking account balance: " << GetBalance() << endl; }  
};  
  
class SavingsAccount : public Account {  
public:  
   SavingsAccount(double d) : Account(d) {}  
   void PrintBalance() { cout << "Savings account balance: " << GetBalance(); }  
};  
  
int main() {  
   // Create objects of type CheckingAccount and SavingsAccount.  
   CheckingAccount *pChecking = new CheckingAccount( 100.00 ) ;  
   SavingsAccount  *pSavings  = new SavingsAccount( 1000.00 );  
  
   // Call PrintBalance using a pointer to Account.  
   Account *pAccount = pChecking;  
   pAccount->PrintBalance();  
  
   // Call PrintBalance using a pointer to Account.  
   pAccount = pSavings;  
   pAccount->PrintBalance();     
}  
```  
  
 En el código anterior, las llamadas a `PrintBalance` son idénticas, excepto por el objeto al que apunta `pAccount`.  Dado que `PrintBalance` es virtual, se llama a la versión de la función definida para cada objeto.  La función `PrintBalance` de las clases derivadas `CheckingAccount` y `SavingsAccount` “reemplaza” la función en la clase base `Account`.  
  
 Si se declara una clase que no proporciona una implementación de reemplazo de la función `PrintBalance`, se usa la implementación predeterminada de la clase base `Account`.  
  
 Las funciones de clases derivadas reemplazan funciones virtuales de clases base solo si son del mismo tipo.  Una función de una clase derivada no puede diferir de una función virtual de una clase base solo en su tipo de valor devuelto; la lista de argumentos también debe ser diferente.  
  
 Al llamar a una función mediante punteros o referencias, se aplican las siguientes reglas:  
  
-   Una llamada a una función virtual se resuelve de acuerdo con el tipo subyacente del objeto para el que se llama.  
  
-   Una llamada a una función no virtual se resuelve de acuerdo con el tipo de puntero o de referencia.  
  
 En el ejemplo siguiente se muestra cómo se comportan las funciones virtuales y no virtuales cuando se llaman mediante punteros:  
  
```  
// deriv_VirtualFunctions2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
  
class Base {  
public:  
   virtual void NameOf();   // Virtual function.  
   void InvokingClass();   // Nonvirtual function.  
};  
  
// Implement the two functions.  
void Base::NameOf() {  
   cout << "Base::NameOf\n";  
}  
  
void Base::InvokingClass() {  
   cout << "Invoked by Base\n";  
}  
  
class Derived : public Base {  
public:  
   void NameOf();   // Virtual function.  
   void InvokingClass();   // Nonvirtual function.  
};  
  
// Implement the two functions.  
void Derived::NameOf() {  
   cout << "Derived::NameOf\n";  
}  
  
void Derived::InvokingClass() {  
   cout << "Invoked by Derived\n";  
}  
  
int main() {  
   // Declare an object of type Derived.  
   Derived aDerived;  
  
   // Declare two pointers, one of type Derived * and the other  
   //  of type Base *, and initialize them to point to aDerived.  
   Derived *pDerived = &aDerived;  
   Base    *pBase    = &aDerived;  
  
   // Call the functions.  
   pBase->NameOf();           // Call virtual function.  
   pBase->InvokingClass();    // Call nonvirtual function.  
   pDerived->NameOf();        // Call virtual function.  
   pDerived->InvokingClass(); // Call nonvirtual function.  
}  
```  
  
### Salida  
  
```  
Derived::NameOf  
Invoked by Base  
Derived::NameOf  
Invoked by Derived  
```  
  
 Observe que, independientemente de si la función `NameOf` se invoca a través de un puntero a `Base` o un puntero a `Derived`, llama a la función para `Derived`.  Llama a la función para `Derived` porque `NameOf` es una función virtual y tanto `pBase` como `pDerived` apuntan a un objeto de tipo `Derived`.  
  
 Dado que solo se llama a funciones virtuales para objetos de tipos de clase, no se puede declarar funciones globales o estáticas como **virtual**.  
  
 La palabra clave **virtual** se puede usar para declarar funciones de reemplazo en una clase derivada, pero no es necesario; los reemplazos de funciones virtuales son siempre virtuales.  
  
 Las funciones virtuales de una clase base se deben definir a menos que se declaren mediante *pure\-specifier*.  \(Para obtener más información sobre las funciones virtuales puras, vea [Clases abstractas](../cpp/abstract-classes-cpp.md)\).  
  
 El mecanismo de llamada a funciones virtuales se puede suprimir calificando explícitamente el nombre de función con el operador de resolución de ámbito \(`::`\).  Considere el ejemplo anterior que implica la clase de `Account`.  Para llamar a `PrintBalance` en la clase base, utilice código como el siguiente:  
  
```  
CheckingAccount *pChecking = new CheckingAccount( 100.00 );  
  
pChecking->Account::PrintBalance();  //  Explicit qualification.  
  
Account *pAccount = pChecking;  // Call Account::PrintBalance  
  
pAccount->Account::PrintBalance();   //  Explicit qualification.  
```  
  
 Ambas llamadas a `PrintBalance` en el ejemplo anterior suprimen el mecanismo de llamada de función virtual.  
  
## Vea también  
 [Acceso a funciones virtuales](../misc/access-to-virtual-functions.md)