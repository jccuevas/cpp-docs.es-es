---
title: typeid (operador) | Documentos de Microsoft
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
- typeid operator
ms.assetid: 8871cee6-d6b9-4301-a5cb-bf3dc9798d61
caps.latest.revision: 10
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
ms.openlocfilehash: 3b987f26e7908c85ca1630059eec434c009c3ef4
ms.contentlocale: es-es
ms.lasthandoff: 09/25/2017

---
# <a name="typeid-operator"></a>typeid (Operador)
## <a name="syntax"></a>Sintaxis  
  
```  
  
      typeid(   
      type-id  
       )  
typeid( expression )  
```  
  
## <a name="remarks"></a>Comentarios  
 El operador `typeid` permite que se determine el tipo de un objeto en tiempo de ejecución.  
  
 El resultado de `typeid` es un **const type_info &**. El valor es una referencia a un **type_info** objeto que representa el *identificador de tipo* o el tipo de la *expresión*, dependiendo de qué forma de `typeid` se utiliza . Vea [type_info (clase)](../cpp/type-info-class.md) para obtener más información.  
  
 El `typeid` operador no funciona con tipos administrados (declaradores abstractos o instancias), consulte [typeid](../windows/typeid-cpp-component-extensions.md) para obtener información sobre cómo obtener el <xref:System.Type> de un tipo especificado.  
  
 El operador `typeid` realiza una comprobación en tiempo de ejecución cuando se aplica a un valor de un tipo de clase polimórfico, en que el tipo verdadero del objeto no se puede determinar mediante la información estática proporcionada. Esos casos son:  
  
-   Una referencia a una clase  
  
-   Un puntero, desreferenciado con *  
  
-   Un puntero con subíndice (es decir, [ ]). (Observe que, normalmente, no es seguro utilizar un subíndice con un puntero a un tipo polimórfico).  
  
 Si el *expresión* apunta a un tipo de clase base, aunque el objeto sea realmente de un tipo derivado de esa clase base, una **type_info** referencia para la clase derivada es el resultado. El *expresión* debe apuntar a un tipo polimórfico (una clase con funciones virtuales). En caso contrario, el resultado es el **type_info** para la clase estática que se hace referencia en el *expresión*. Además, el puntero se debe desreferenciar para que se utilice el objeto al que señala. Si no se desreferencia el puntero, el resultado será el **type_info** para el puntero, no lo que apunta a. Por ejemplo:  
  
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
  
 Si el *expresión* se desreferencia un puntero, y que el valor del puntero es cero, **typeid** produce una [bad_typeid (excepción)](../cpp/bad-typeid-exception.md). Si el puntero no señala a un objeto válido, un `__non_rtti_object` excepción, que indica un intento de analizar el RTTI que activó un error (como la infracción de acceso), porque el objeto es de algún modo no válido (puntero incorrecto o el código no se compilaron con [/GR](../build/reference/gr-enable-run-time-type-information.md)).  
  
 Si el *expresión* no es un puntero ni una referencia a una clase base del objeto, el resultado es un **type_info** referencia que representa el tipo estático de la *expresión*. El *tipo estático* de una expresión hace referencia la para el tipo de una expresión tal y como se conoce en tiempo de compilación. La semántica de ejecución se omite cuando se evalúa el tipo estático de una expresión. Además, las referencias se omiten cuando es posible al determinar el tipo estático de una expresión:  
  
```  
// expre_typeid_Operator_2.cpp  
#include <typeinfo>  
  
int main()  
{  
   typeid(int) == typeid(int&); // evaluates to true  
}  
```  
  
 **typeid** también puede usarse en las plantillas para determinar el tipo de un parámetro de plantilla:  
  
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
  
## <a name="see-also"></a>Vea también  
 [Información de tipos en tiempo de ejecución](../cpp/run-time-type-information.md)   
 [Palabras clave](../cpp/keywords-cpp.md)
