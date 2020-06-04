---
title: 'Cómo: especificar un parámetro out'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
ms.openlocfilehash: 4bd6ad1d3009adcc124bdeb90d9d67de07112de2
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "79545448"
---
# <a name="how-to-specify-an-out-parameter"></a>Cómo: especificar un parámetro out

En este ejemplo se muestra cómo especificar que un parámetro de función es un parámetro `out` y cómo llamar a esa función desde C# un programa.

Un parámetro `out` se especifica en C++ mediante <xref:System.Runtime.InteropServices.OutAttribute>.

## <a name="example"></a>Ejemplo

La primera parte de este ejemplo crea un C++ archivo dll. Define un tipo que contiene una función con un parámetro `out`.

```cpp
// cpp_out_param.cpp
// compile with: /LD /clr
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

Este archivo de código fuente C# es un cliente que utiliza C++ el componente creado en el ejemplo anterior.

```csharp
// cpp_out_param_2.cs
// compile with: /reference:cpp_out_param.dll
using System;
class TestClass {
   public static void Main() {
      String t;
      TestStruct.Test(out t);
      System.Console.WriteLine(t);
   }
}
```

```Output
a string
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
