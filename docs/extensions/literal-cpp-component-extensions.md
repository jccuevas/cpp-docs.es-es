---
title: literal (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- literal
- literal_cpp
helpviewer_keywords:
- literal keyword [C++]
ms.assetid: 6b1a1f36-2e1d-4a23-8eb6-172f4f3c477f
ms.openlocfilehash: d567f8270dcb8965ed2f882c9a0c005f295fc619
ms.sourcegitcommit: c4528a7424d35039454f17778baf1b5f98fbbee7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/01/2020
ms.locfileid: "79545460"
---
# <a name="literal-ccli-and-ccx"></a>literal (C++/CLI y C++/CX)

Una variable (miembro de datos) marcada como **literal** en una compilación **/clr** es el equivalente nativo de una variable **static const**.

## <a name="all-platforms"></a>Todas las plataformas

### <a name="remarks"></a>Observaciones

(No hay notas para esta característica de lenguaje que se apliquen a todos los runtimes).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

### <a name="remarks"></a>Observaciones

(No hay notas para esta característica de lenguaje que solo se apliquen a Windows Runtime).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

## <a name="remarks"></a>Observaciones

Un miembro de datos marcado como **literal** debe inicializarse al declararse y el valor debe ser una constante entera, una enumeración o un tipo de cadena. La conversión del tipo de la expresión de inicialización al tipo del miembro de datos estático const no debe requerir una conversión definida por el usuario.

No se asigna memoria para el campo literal en tiempo de ejecución; el compilador solo inserta su valor en los metadatos para la clase.

Una variable marcada como **static const** no estará disponible en los metadatos para otros compiladores.

Para obtener más información, consulte los artículos sobre [Static](../cpp/storage-classes-cpp.md) y [const](../cpp/const-cpp.md).

**literal** es una palabra clave contextual. Consulte [Context-Sensitive Keywords](context-sensitive-keywords-cpp-component-extensions.md) (Palabras clave contextuales) para obtener más información.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra que una variable **literal** implica **static**.

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

En el siguiente ejemplo se muestra el efecto de literal en los metadatos:

```cpp
// mcppv2_literal2.cpp
// compile with: /clr /LD
public ref struct A {
   literal int lit = 0;
   static const int sc = 1;
};
```

Tenga en cuenta la diferencia en los metadatos para `sc` y `lit`: la directiva `modopt` se aplica a `sc`, por lo que otros compiladores pueden hacerle caso omiso.

```
.field public static int32 modopt([mscorlib]System.Runtime.CompilerServices.IsConst) sc = int32(0x0000000A)
```

```
.field public static literal int32 lit = int32(0x0000000A)
```

## <a name="example"></a>Ejemplo

En el siguiente ejemplo, creado en C#, se hace referencia a los metadatos creados en el ejemplo anterior y se muestra el efecto de las variables **literal** y **static const**:

```csharp
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

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)