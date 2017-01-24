---
title: "Operador address-of: &amp; | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "address-of"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "& (operador)"
  - "& (operador), address-of (operador)"
  - "address-of (operador) (&)"
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Operador address-of: &amp;
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
& cast-expression  
```  
  
## Comentarios  
 El operador unario address\-of \(**&**\) toma la dirección de su operando.  El operando del operador address\-of puede ser un designador de función o un valor L que designe un objeto que no es un campo de bits y no se declara con el especificador de clase de almacenamiento **register**.  
  
 El operador address\-of solo se puede aplicar a variables con tipos fundamentales, de estructura, de clase o de unión que se declaren en el nivel de ámbito de archivo o para referencias de matriz de subíndice.  En estas expresiones, se puede agregar o quitar de la expresión address\-of una expresión constante que no incluya el operador address\-of.  
  
 Cuando se aplica a funciones o valores L, el resultado de la expresión es un tipo de puntero \(un valor R\) derivado del tipo del operando.  Por ejemplo, si el operando es de tipo `char`, el resultado de la expresión es de tipo puntero a `char`.  El operator address\-of, aplicado a objetos **const** o `volatile`, se evalúa como **const** `type` **\*** o `volatile` `type` **\***, donde `type` es el tipo del objeto original.  
  
 Cuando el operador address\-of se aplica a un [nombre completo](http://msdn.microsoft.com/es-es/3fefb16d-8120-4627-8b3f-3d90fbdcd1df), el resultado depende de si *qualified\-name* especifica un miembro estático.  En ese caso, el resultado es un puntero al tipo especificado en la declaración del miembro.  Si el miembro no es estático, el resultado es un puntero al *name* del miembro de la clase que se indica mediante el elemento *qualified\-class\-name*. \(Vea [Expresiones primarias](../cpp/primary-expressions.md) para obtener más información sobre el elemento *qualified\-class\-name*\). En el fragmento de código siguiente se muestra cómo difiere el resultado, dependiendo de si el miembro es estático:  
  
```  
// expre_Address_Of_Operator.cpp  
// C2440 expected  
class PTM {  
public:  
           int   iValue;  
    static float fValue;  
};  
  
int main() {  
   int   PTM::*piValue = &PTM::iValue;  // OK: non-static  
   float PTM::*pfValue = &PTM::fValue;  // C2440 error: static  
   float *spfValue     = &PTM::fValue;  // OK  
}  
```  
  
 En este ejemplo, la expresión `&PTM::fValue` proporciona el tipo `float *` en lugar de `float PTM::*`, porque `fValue` es un miembro estático.  
  
 La dirección de una función sobrecargada se puede tomar solo cuando está claro a qué versión de la función se hace referencia.  Vea [Dirección de funciones sobrecargadas](../misc/address-of-overloaded-functions.md) para obtener información sobre cómo obtener la dirección de una función sobrecargada concreta.  
  
 Al aplicar el operator address\-of a un tipo de referencia se obtiene el mismo resultado que al aplicar el operador al objeto al que se enlaza la referencia.  Por ejemplo:  
  
## Ejemplo  
  
```  
// expre_Address_Of_Operator2.cpp  
// compile with: /EHsc  
#include <iostream>  
using namespace std;  
int main() {  
   double d;        // Define an object of type double.  
   double& rd = d;  // Define a reference to the object.  
  
   // Obtain and compare their addresses  
   if( &d == &rd )  
      cout << "&d equals &rd" << endl;  
}  
```  
  
## Salida  
  
```  
&d equals &rd  
```  
  
 En el ejemplo siguiente se usa el operator address\-of para pasar un argumento de puntero a una función:  
  
```  
// expre_Address_Of_Operator3.cpp  
// compile with: /EHsc  
// Demonstrate address-of operator &  
  
#include <iostream>  
using namespace std;  
  
// Function argument is pointer to type int  
int square( int *n ) {  
   return (*n) * (*n);  
}  
  
int main() {  
   int mynum = 5;  
   cout << square( &mynum ) << endl;   // pass address of int  
}  
```  
  
## Salida  
  
```  
25  
```  
  
## Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Operadores de C\+\+](../misc/cpp-operators.md)   
 [Operadores de C\+\+, precedencia y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Declarador de referencia a un valor L: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Operadores de direccionamiento indirecto y address\-of](../c-language/indirection-and-address-of-operators.md)