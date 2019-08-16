---
title: Procedimiento Mejora del rendimiento con genéricos (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- performance, C++
- C++, performance
- C++, generics
- generics [C++], performance
ms.assetid: f14a175b-301f-46cc-86e4-c82d35f9aa3e
ms.openlocfilehash: 958da08716022bedaa8d0fe217814fa2bd86c065
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515720"
---
# <a name="how-to-improve-performance-with-generics-ccli"></a>Procedimiento Mejora del rendimiento con genéricos (C++/CLI)

Con los genéricos, puede crear código reutilizable basado en un parámetro de tipo. El tipo real del parámetro de tipo se aplaza hasta que lo invoca el código de cliente. Para más información sobre genéricos, vea [Generics](generics-cpp-component-extensions.md).

En este artículo se describe cómo los genéricos pueden ayudar a aumentar el rendimiento de una aplicación que usa colecciones.

## <a name="example"></a>Ejemplo

.NET Framework incluye muchas clases de colecciones en el espacio de nombres <xref:System.Collections?displayProperty=fullName>. La mayoría de estas colecciones funcionan en objetos de tipo <xref:System.Object?displayProperty=fullName>. Esto permite que las colecciones almacenen cualquier tipo, dado que todos los tipos de .NET Framework, incluso los tipos de valor, se derivan de <xref:System.Object?displayProperty=fullName>. Sin embargo, este enfoque presenta dos desventajas.

En primer lugar, si la colección va a almacenar tipos de valor como enteros, se debe aplicar al valor una conversión boxing antes de agregarlo a la colección y quitarle la conversión boxing cuando se recupere de la colección. Estas operaciones son costosas.

En segundo lugar, no hay manera de controlar qué tipos se pueden agregar a una colección. Es perfectamente válido agregar un entero y una cadena a la misma colección, aunque esto no fuera probablemente lo que se pretendía. Por lo tanto, para que el código tenga seguridad de tipos, debe comprobar que el tipo recuperado de la colección sea realmente lo que se esperaba.

En el ejemplo de código siguiente se muestran las dos desventajas principales de las colecciones de .NET Framework antes de los genéricos.

```cpp
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

El nuevo espacio de nombres <xref:System.Collections.Generic?displayProperty=fullName> contiene muchas de las mismas colecciones que se encuentran en el espacio de nombres <xref:System.Collections?displayProperty=fullName>, pero se han modificado para aceptar parámetros de tipo genérico. De esta forma se eliminan las dos desventajas de las colecciones no genéricas: la conversión boxing y unboxing de los tipos de valor y la imposibilidad de especificar que los tipos se almacenen en las colecciones. Las operaciones en las dos colecciones son idénticas; la única diferencia es como se crea una instancia de ellas.

Compare el ejemplo escrito anteriormente con este ejemplo que usa una colección <xref:System.Collections.Generic.Stack%601> genérica. En colecciones grandes a las que se accede con frecuencia, el rendimiento en este ejemplo será bastante mayor que en el ejemplo anterior.

```cpp
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

[Genéricos](generics-cpp-component-extensions.md)