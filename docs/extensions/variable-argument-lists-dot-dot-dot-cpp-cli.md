---
title: Listas de argumentos de variables (...) (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- variable argument lists
- parameter arrays
ms.assetid: db1a27f4-02a8-4318-8690-1f2893f52b38
ms.openlocfilehash: dfe40d20fc8bb795b0e530b3288b1c2101bc55ab
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171884"
---
# <a name="variable-argument-lists--ccli"></a>Listas de argumentos de variables (...) (C++/CLI)

En este ejemplo se muestra cómo puede usar la sintaxis `...` en C++/CLI para implementar las funciones con un número variable de argumentos.

> [!NOTE]
> Este tema corresponde a C++/CLI. Para obtener información sobre el uso de `...` en la norma ISO de C++, consulte [Puntos suspensivos y plantillas variádicas](../cpp/ellipses-and-variadic-templates.md). En cuanto a los puntos suspensivos y los argumentos predeterminados, consulte [Expresiones postfijas](../cpp/postfix-expressions.md).

El parámetro que usa `...` debe ser el último de la lista de parámetros.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
// mcppv2_paramarray.cpp
// compile with: /clr
using namespace System;
double average( ... array<Int32>^ arr ) {
   int i = arr->GetLength(0);
   double answer = 0.0;

   for (int j = 0 ; j < i ; j++)
      answer += arr[j];

   return answer / i;
}

int main() {
   Console::WriteLine("{0}", average( 1, 2, 3, 6 ));
}
```

```Output
3
```

## <a name="code-example"></a>Ejemplo de código

En el siguiente ejemplo se muestra cómo llamar desde C# a una función de Visual C++ que toma un número de argumentos variable.

```cpp
// mcppv2_paramarray2.cpp
// compile with: /clr:safe /LD
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};
```

Se puede llamar a la función `f` desde C# o Visual Basic, por ejemplo, como si fuera una función que puede tomar un número de argumentos variable.

En C#, un argumento que se pasa a un parámetro `ParamArray` al que puede llamar un número de argumentos variable. El ejemplo de código siguiente está en C#.

```csharp
// mcppv2_paramarray3.cs
// compile with: /r:mcppv2_paramarray2.dll
// a C# program

public class X {
   public static void Main() {
      // Visual C# will generate a String array to match the
      // ParamArray attribute
      C myc = new C();
      myc.f("hello", "there", "world");
   }
}
```

Una llamada a `f` en Visual C++ puede pasar una matriz inicializada o una matriz de longitud variable.

```cpp
// mcpp_paramarray4.cpp
// compile with: /clr
using namespace System;

public ref class C {
public:
   void f( ... array<String^>^ a ) {}
};

int main() {
   C ^ myc = gcnew C();
   myc->f("hello", "world", "!!!");
}
```

## <a name="see-also"></a>Consulte también

[Matrices](arrays-cpp-component-extensions.md)
