---
title: "typeid (Operador) | Microsoft Docs"
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
  - "typeid (operador)"
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# typeid (Operador)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Sintaxis  
  
```  
  
      typeid(   
      type-id  
       )  
typeid( expression )  
```  
  
## Comentarios  
 El operador `typeid` permite que se determine el tipo de un objeto en tiempo de ejecución.  
  
 El resultado de `typeid` es **const type\_info&**.  El valor es una referencia a un objeto **type\_info** que representa el *type\-id* o el tipo de *expression*, dependiendo de la forma en que se use `typeid`.  Vea [type\_info \(Clase\)](../cpp/type-info-class.md) para obtener más información.  
  
 El operador de `typeid` no funciona con los tipos administrados \(instancias o declaradores abstractos\); vea [typeid](../Topic/typeid%20%20\(C++%20Component%20Extensions\).md) para obtener información sobre cómo se obtiene <xref:System.Type> de un tipo especificado.  
  
 El operador `typeid` realiza una comprobación en tiempo de ejecución cuando se aplica a un valor de un tipo de clase polimórfico, en que el tipo verdadero del objeto no se puede determinar mediante la información estática proporcionada.  Esos casos son:  
  
-   Una referencia a una clase  
  
-   Un puntero, desreferenciado con \*  
  
-   Un puntero con subíndice \(es decir, \[ \]\). \(Observe que, normalmente, no es seguro utilizar un subíndice con un puntero a un tipo polimórfico\).  
  
 Si *expression* señala a un tipo de clase base, aunque el objeto sea realmente de un tipo derivado de esa clase base, el resultado es una referencia de **type\_info** para la clase derivada.  El elemento *expression* debe señalar a un tipo polimórfico \(una clase con funciones virtuales\).  De lo contrario, el resultado es el **type\_info** para la clase estática a que se hace referencia en *expression*.  Además, el puntero se debe desreferenciar para que se utilice el objeto al que señala.  Si no se desreferencia el puntero, el resultado será el **type\_info** para el puntero, no el objeto al que señala.  Por ejemplo:  
  
```  
// expre_typeid_Operator.cpp  
// compile with: /GR /EHsc  
#include <iostream>  
#include <typeinfo.h>  
  
class Base {  
public:  
   virtual void vvfunc() {}  
};  
  
class Derived : public Base {};  
  
using namespace std;  
int main() {  
   Derived* pd = new Derived;  
   Base* pb = pd;  
   cout << typeid( pb ).name() << endl;   //prints "class Base *"  
   cout << typeid( *pb ).name() << endl;   //prints "class Derived"  
   cout << typeid( pd ).name() << endl;   //prints "class Derived *"  
   cout << typeid( *pd ).name() << endl;   //prints "class Derived"  
   delete pd;  
}  
```  
  
 Si *expression* desreferencia un puntero y el valor de ese puntero es cero, **typeid** produce una [excepción bad\_typeid](../cpp/bad-typeid-exception.md).  Si el puntero no señala a un objeto válido, se produce una excepción `__non_rtti_object`, que indica un intento de analizar el RTTI que activó un error \(por ejemplo, una infracción de acceso\), porque el objeto es de algún modo no válido \(el puntero incorrecto o el código no se compilaron con [\/GR](../build/reference/gr-enable-run-time-type-information.md)\).  
  
 Si *expression* no es un puntero ni una referencia a una clase base del objeto, el resultado es una referencia de **type\_info** que representa el tipo estático de *expression*.  El elemento *static type* de una expresión se refiere al tipo de una expresión cuando se conoce en tiempo de compilación.  La semántica de ejecución se omite cuando se evalúa el tipo estático de una expresión.  Además, las referencias se omiten cuando es posible al determinar el tipo estático de una expresión:  
  
```  
// expre_typeid_Operator_2.cpp  
#include <typeinfo>  
  
int main()  
{  
   typeid(int) == typeid(int&); // evaluates to true  
}  
```  
  
 **typeid** también se puede utilizar en plantillas para determinar el tipo de un parámetro de plantilla:  
  
```  
// expre_typeid_Operator_3.cpp  
// compile with: /c  
#include <typeinfo>  
template < typename T >   
T max( T arg1, T arg2 ) {  
   cout << typeid( T ).name() << "s compared." << endl;  
   return ( arg1 > arg2 ? arg1 : arg2 );  
}  
```  
  
## Vea también  
 [Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)