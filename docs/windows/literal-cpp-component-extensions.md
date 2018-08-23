---
title: literal (extensiones de componentes de C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
dev_langs:
- C++
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 76a57261b28679c4f05b677dc7b49008535c921b
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42596451"
---
# <a name="literal-c-component-extensions"></a>literal (Extensiones de componentes de C++)

Una variable (miembro de datos) marcados como **literal** en un **/CLR** compilación es el equivalente nativo de un **static const** variable.

## <a name="all-platforms"></a>Todas las plataformas

### <a name="remarks"></a>Comentarios

(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes.)

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Comentarios

(No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

## <a name="remarks"></a>Comentarios

Un miembro de datos marcada como **literal** debe inicializarse cuando se declara y el valor debe ser una constante integral, enumeración o tipo de cadena. Conversión del tipo de la expresión de inicialización para el tipo del miembro de datos const estático no debe requerir una conversión definida por el usuario.

No se asigna memoria para el campo literal en tiempo de ejecución; el compilador solo inserta su valor en los metadatos de la clase.

Una variable marcada **static const** no estará disponible en los metadatos a otros compiladores.

Para obtener más información, consulte [estático](../cpp/storage-classes-cpp.md) y [const](../cpp/const-cpp.md).

**literal** es una palabra clave contextual. Consulte [palabras clave contextuales](../windows/context-sensitive-keywords-cpp-component-extensions.md) para obtener más información.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra que un **literal** variable implica **estático**.

```cpp
// mcppv2_literal.cpp
// compile with: /clr
ref struct X {
   literal int i = 4;
};

int main() {
   int value = X::i;
}
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra el efecto de literal en los metadatos:

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

Tenga en cuenta la diferencia en los metadatos de `sc` y `lit`: el `modopt` directiva se aplica a `sc`, lo que significa que se puede hacer caso omiso otros compiladores.

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)  
```

```
.field public static literal int32 lit = int32(0x0000000A)  
```

## <a name="example"></a>Ejemplo

El ejemplo siguiente, creado en C#, hace referencia a los metadatos creados en el ejemplo anterior y muestra el efecto de **literal** y **static const** variables:

```cs
// mcppv2_literal3.cs
// compile with: /reference:mcppv2_literal2.dll
// A C# program
class B {
   public static void Main() {
      // OK
      System.Console.WriteLine(A.lit);
      System.Console.WriteLine(A.sc);

      // C# does not enforce C++ const
      A.sc = 9;
      System.Console.WriteLine(A.sc);

      // C# enforces const for a literal
      A.lit = 9;   // CS0131

      // you can assign a C++ literal variable to a C# const variable
      const int i = A.lit;
      System.Console.WriteLine(i);

      // but you cannot assign a C++ static const variable
      // to a C# const variable
      const int j = A.sc;   // CS0133
      System.Console.WriteLine(j);
   }
}
```

## <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

## <a name="see-also"></a>Vea también

[Extensiones de componentes para plataformas de tiempo de ejecución](../windows/component-extensions-for-runtime-platforms.md)