---
title: Semántica de pila de C++ para tipos de referencia | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- reference types, C++ stack semantics for
ms.assetid: 319a1304-f4a4-4079-8b84-01cec847d531
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: b3ed886d1bdeb4972122049854b5d288767aa5b8
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111359"
---
# <a name="c-stack-semantics-for-reference-types"></a>Semántica de pila de C++ para los tipos de referencia
Antes de Visual C++ 2005, una instancia de un tipo de referencia sólo se creara con el `new` montón restante de operador, que se creó el objeto en los elementos no utilizados. Sin embargo, ahora puede crear una instancia de un tipo de referencia con la misma sintaxis que utilizaría para crear una instancia de un tipo nativo en la pila. Por lo tanto, no es necesario usar [gcnew nueva, ref](../windows/ref-new-gcnew-cpp-component-extensions.md) para crear un objeto de un tipo de referencia. Y cuando el objeto queda fuera del ámbito, el compilador llama al destructor del objeto.  
  
## <a name="remarks"></a>Comentarios  
 Cuando crea una instancia de un tipo de referencia mediante la semántica de pila, el compilador crea internamente la instancia en el montón de elementos no utilizados (mediante `gcnew`).  
  
 Cuando el tipo de valor devuelto o firma de una función incluye una instancia de un tipo de referencia por valor, la función se marcarán en los metadatos que requieran un tratamiento especial (con modreq). Este tratamiento especial es actualmente sólo proporcionadas por los clientes de Visual C++; otros lenguajes no admiten actualmente consumo funciones o datos que usan los tipos de referencia creados con semántica de pila.  
  
 Una razón para utilizar `gcnew` (asignación dinámica) en lugar de pila semántica sería si el tipo no tenga un destructor. Además, el uso de los tipos de referencia creados con semántica de pila en las firmas de función no sería posible si desea que las funciones para utilizarse en lenguajes diferentes de Visual C++.  
  
 El compilador no generará un constructor de copias para un tipo de referencia. Por lo tanto, si define una función que usa un tipo de referencia por valor en la firma, debe definir un constructor de copias para el tipo de referencia. Un constructor de copias para un tipo de referencia tiene una firma de la forma siguiente: `R(R%){}`.  
  
 El compilador no generará un operador de asignación predeterminado para un tipo de referencia. Un operador de asignación permite crear un objeto utilizando semántica de pila y se inicializa con un objeto existente que se creó mediante la semántica de pila. Un operador de asignación para un tipo de referencia tiene una firma de la forma siguiente: `void operator=( R% ){}`.  
  
 Si el destructor de su tipo libera los recursos críticos y usar semántica de pila para los tipos de referencia, no es necesario llamar explícitamente al destructor (o llamar a `delete`). Para obtener más información acerca de destructores en tipos de referencia, vea [destructores y finalizadores en cómo: definir y utilizar clases y structs (C++ / CLI)](../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Destructors_and_finalizers).  
  
 Un operador de asignación generados por el compilador seguirá las reglas habituales de C++ estándares con las siguientes adiciones:  
  
-   Los datos no estáticos miembros cuyo tipo es un identificador de un tipo de referencia será shallow copiados (se trata como un miembro de datos no estáticos cuyo tipo es un puntero).  
  
-   Copia de cualquier miembro de datos no estáticos cuyo tipo sea que un tipo de valor será superficial.  
  
-   Cualquier miembro de datos no estáticos cuyo tipo es una instancia de un tipo de referencia invocará una llamada al constructor de copias del tipo de referencia.  
  
 El compilador también ofrece un `%` operador unario para convertir una instancia de un tipo de referencia creado mediante la semántica de pila en su tipo de identificador subyacente.  
  
 Los siguientes tipos de referencia no están disponibles para su uso con semántica de pila:  
  
-   [delegate (Extensiones de componentes de C++)](../windows/delegate-cpp-component-extensions.md)  
  
-   [Matrices](../windows/arrays-cpp-component-extensions.md)  
  
-   <xref:System.String>  
  
## <a name="example"></a>Ejemplo  
  
### <a name="description"></a>Descripción  
 El ejemplo de código siguiente muestra cómo declarar instancias de tipos de referencia con semántica de pila, el operador de asignación y funciona de constructor de copia y cómo inicializar una referencia de seguimiento con el tipo de referencia creado mediante la semántica de pila.  
  
### <a name="code"></a>Código  
  
```  
// stack_semantics_for_reference_types.cpp  
// compile with: /clr  
ref class R {  
public:  
   int i;  
   R(){}  
  
   // assignment operator  
   void operator=(R% r) {  
      i = r.i;  
   }  
  
   // copy constructor  
   R(R% r) : i(r.i) {}  
};  
  
void Test(R r) {}   // requires copy constructor  
  
int main() {  
   R r1;  
   r1.i = 98;  
  
   R r2(r1);   // requires copy constructor  
   System::Console::WriteLine(r1.i);  
   System::Console::WriteLine(r2.i);  
  
   // use % unary operator to convert instance using stack semantics  
   // to its underlying handle  
   R ^ r3 = %r1;  
   System::Console::WriteLine(r3->i);  
  
   Test(r1);  
  
   R r4;  
   R r5;  
   r5.i = 13;  
   r4 = r5;   // requires a user-defined assignment operator  
   System::Console::WriteLine(r4.i);  
  
   // initialize tracking reference  
   R % r6 = r4;  
   System::Console::WriteLine(r6.i);  
}  
```  
  
### <a name="output"></a>Salida  
  
```  
98  
98  
98  
13  
13  
```  
  
## <a name="see-also"></a>Vea también  
 [Clases y structs](../windows/classes-and-structs-cpp-component-extensions.md)