---
title: 'Cómo: mejorar el rendimiento con genéricos (Visual C++) | Documentos de Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- performance, C++
- Visual C++, performance
- Visual C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: da74cce5f41c3399fb102180cfdfe8c1215c8bf9
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="how-to-improve-performance-with-generics-visual-c"></a>Cómo: Mejorar el rendimiento con genéricos (Visual C++)
Con los genéricos, puede crear código reutilizable, basado en un parámetro de tipo. El tipo real del parámetro de tipo se aplaza hasta que se llama a un código de cliente. Para obtener más información sobre genéricos, vea [genéricos](../windows/generics-cpp-component-extensions.md).  
  
 Este artículo tratará sobre cómo pueden ayudar a aumentar el rendimiento de una aplicación que usa colecciones genéricos.  
  
## <a name="example"></a>Ejemplo  
 .NET Framework incluye muchas clases de colección en el <xref:System.Collections?displayProperty=fullName> espacio de nombres. La mayoría de estas colecciones operan sobre objetos de tipo <xref:System.Object?displayProperty=fullName>. Esto permite que las colecciones almacenar cualquier tipo, ya que todos los tipos de .NET Framework, incluso los tipos de valor, se derivan de <xref:System.Object?displayProperty=fullName>. Sin embargo, hay dos inconvenientes de este enfoque.  
  
 En primer lugar, si la colección es almacenar los tipos de valor como enteros, el valor debe ser antes de que se va a agregar a la colección a una conversión boxing y conversión unboxing cuando el valor se recupera de la colección. Estas son operaciones costosas.  
  
 En segundo lugar, no hay ninguna manera de controlar qué tipos se pueden agregar a una colección. Es perfectamente válido para agregar un número entero y una cadena a la misma colección, aunque es probable que no lo que se pretendía. Por lo tanto, para el código tener seguridad de tipos, tener que comprobar que el tipo que se recuperan de la colección es realmente lo que se esperaba.  
  
 En el ejemplo de código siguiente se muestra el dos inconvenientes principales de las colecciones de .NET Framework antes de genéricos.  
  
```  
// perf_pre_generics.cpp  
// compile with: /clr  
  
using namespace System;  
using namespace System::Collections;  
  
int main()  
{  
    // This Stack can contain any type.  
    Stack ^s = gcnew Stack();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
  
    // Push a String to the same Stack.  
    // The Stack now contains two different data types.  
    s->Push("Seven");  
  
    // Pop the items off the Stack.  
    // The item is returned as an Object, so a cast is  
    // necessary to convert it to its proper type.  
    while (s->Count> 0)  
    {  
        Object ^o = s->Pop();  
        if (o->GetType() == Type::GetType("System.String"))  
        {  
            Console::WriteLine("Popped a String: {0}", (String ^)o);  
        }  
        else if (o->GetType() == Type::GetType("System.Int32"))  
        {  
            Console::WriteLine("Popped an int: {0}", (int)o);  
        }  
        else  
        {  
            Console::WriteLine("Popped an unknown type!");  
        }  
    }  
}  
```  
  
```Output  
Popped a String: Seven  
Popped an int: 7  
```  
  
## <a name="example"></a>Ejemplo  
 El nuevo <xref:System.Collections.Generic?displayProperty=fullName> espacio de nombres contiene muchas de las colecciones mismo que se encuentra en la <xref:System.Collections?displayProperty=fullName> espacio de nombres, pero se han modificado para aceptar parámetros de tipo genérico. Esto elimina las dos desventajas de las colecciones no genéricas: la conversión boxing y unboxing de tipos de valor y a la incapacidad para especificar los tipos que se almacenará en las colecciones. Las operaciones en las dos colecciones son idénticas; sólo se diferencian en cómo se crea una instancia.  
  
 Compárelo con el ejemplo escrito anteriormente con este ejemplo se usa un tipo genérico <xref:System.Collections.Generic.Stack%601> colección. En las colecciones grandes que se accede con frecuencia, el rendimiento de este ejemplo será significativamente mayor que el ejemplo anterior.  
  
```  
// perf_post_generics.cpp  
// compile with: /clr  
  
#using <System.dll>  
  
using namespace System;  
using namespace System::Collections::Generic;  
  
int main()  
{  
    // This Stack can only contain integers.  
    Stack<int> ^s = gcnew Stack<int>();  
  
    // Push an integer to the Stack.  
    // A boxing operation is performed here.  
    s->Push(7);  
    s->Push(14);  
  
    // You can no longer push a String to the same Stack.  
    // This will result in compile time error C2664.  
    //s->Push("Seven");  
  
    // Pop an item off the Stack.  
    // The item is returned as the type of the collection, so no  
    // casting is necessary and no unboxing is performed for  
    // value types.  
    int i = s->Pop();  
    Console::WriteLine(i);  
  
    // You can no longer retrieve a String from the Stack.  
    // This will result in compile time error C2440.  
    //String ^str = s->Pop();  
}  
```  
  
```Output  
14  
```  
  
## <a name="see-also"></a>Vea también  
 [Genéricos](../windows/generics-cpp-component-extensions.md)