---
title: 'Operador Address-of: &amp; | Documentos de Microsoft'
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
f1_keywords:
- '&'
dev_langs:
- C++
helpviewer_keywords:
- address-of operator (&)
- '& operator'
- '& operator [C++], address-of operator'
ms.assetid: 2828221a-15f6-4acc-87fe-25e34feebb88
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 814b21839ac851e942aaee34ed28fd43facb418a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="address-of-operator-amp"></a>Operador Address-of:&amp;
## <a name="syntax"></a>Sintaxis  
  
```  
& cast-expression  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador unario address-of (**&**) toma la dirección de su operando. El operando del operador address-of puede ser un designador de función o un valor L que designe un objeto que no es un campo de bits y no se declara con el especificador de clase de almacenamiento **register**.  
  
 El operador address-of solo se puede aplicar a variables con tipos fundamentales, de estructura, de clase o de unión que se declaren en el nivel de ámbito de archivo o para referencias de matriz de subíndice. En estas expresiones, se puede agregar o quitar de la expresión address-of una expresión constante que no incluya el operador address-of.  
  
 Cuando se aplica a funciones o valores L, el resultado de la expresión es un tipo de puntero (un valor R) derivado del tipo del operando. Por ejemplo, si el operando es de tipo `char`, el resultado de la expresión es de tipo puntero a `char`. El operador address-of, aplicado a **const** o `volatile` los objetos, se evalúa como **const** `type`  **\***  o `volatile` `type`  **\*** , donde `type` es el tipo del objeto original.  
  
 Cuando se aplica el operador address-of a una [nombre completo](http://msdn.microsoft.com/en-us/3fefb16d-8120-4627-8b3f-3d90fbdcd1df), el resultado depende de si la *nombre calificado* especifica un miembro estático. En ese caso, el resultado es un puntero al tipo especificado en la declaración del miembro. Si el miembro no es estático, el resultado es un puntero al miembro *nombre* de la clase indicada por *qualified-class-name*. (Consulte [expresiones primarias](../cpp/primary-expressions.md) para obtener más información acerca de *qualified-class-name*.) En el fragmento de código siguiente se muestra cómo difiere el resultado, dependiendo de si el miembro es estático:  
  
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
  
 La dirección de una función sobrecargada se puede tomar solo cuando está claro a qué versión de la función se hace referencia. Vea [sobrecarga de funciones](function-overloading.md) para obtener información acerca de cómo obtener la dirección de una determinada función sobrecargada.  
  
 Al aplicar el operator address-of a un tipo de referencia se obtiene el mismo resultado que al aplicar el operador al objeto al que se enlaza la referencia. Por ejemplo:  
  
## <a name="example"></a>Ejemplo  
  
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
  
## <a name="output"></a>Salida  
  
```  
&d equals &rd  
```  
  
 En el ejemplo siguiente se usa el operator address-of para pasar un argumento de puntero a una función:  
  
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
  
## <a name="output"></a>Salida  
  
```  
25  
```  
  
## <a name="see-also"></a>Vea también  
 [Expresiones con operadores unarios](../cpp/expressions-with-unary-operators.md)   
 [Los operadores integrados de C++, prioridad y asociatividad](../cpp/cpp-built-in-operators-precedence-and-associativity.md)   
 [Declarador de referencia lvalue: &](../cpp/lvalue-reference-declarator-amp.md)   
 [Operadores de direccionamiento indirecto y address-of](../c-language/indirection-and-address-of-operators.md)
