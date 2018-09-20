---
title: 'Cómo: especificar un fuera parámetro | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- function parameters
- out parameters
ms.assetid: 02862448-603c-4e9d-a5c5-b45fe38446e3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 3af9c1d10206e89b0ad8462bd95fdf3b6062d713
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46419508"
---
# <a name="how-to-specify-an-out-parameter"></a>Cómo: Especificar un parámetro out

En este ejemplo se muestra cómo especificar que un parámetro de función es un parámetro de salida y cómo llamar a esa función desde un programa de C#.

Se especificó un parámetro out en Visual C++ con <xref:System.Runtime.InteropServices.OutAttribute> .

## <a name="example"></a>Ejemplo

La primera parte de este ejemplo es un archivo DLL de Visual C++ con un tipo que contiene una función con un parámetro de salida.

```
// cpp_out_param.cpp
// compile with: /LD /clr:safe
using namespace System;
public value struct TestStruct {
   static void Test([Runtime::InteropServices::Out] String^ %s) {
      s = "a string";
   }
};
```

## <a name="example"></a>Ejemplo

Se trata de un cliente de C# que utiliza el componente de Visual C++ creado en el ejemplo anterior.

```
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

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)