---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: bc44feb97223de47f45734f75777ee040d0ebdd8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50534581"
---
# <a name="clrcall"></a>__clrcall

**Específicos de Microsoft**

Especifica que solo se puede llamar a una función desde código administrado.  Use **__clrcall** para todas las funciones virtuales solo se llamará desde código administrado. Sin embargo esta convención de llamada no se puede utilizar para las funciones a las que llamará desde código nativo.

Use **__clrcall** para mejorar el rendimiento cuando se llama desde una función administrada a una función administrada virtual o desde una función administrada a una función administrada mediante puntero.

Los puntos de entrada son funciones independientes generadas por el compilador. Si una función tiene puntos de entrada nativos y administrados, uno de ellos será la función real con la implementación de la función. La otra función será una función independiente (un código thunk) que llama a la función real y deja que Common Language Runtime realice PInvoke. Cuando se marca una función como **__clrcall**, indicar la implementación de la función debe ser MSIL y que la función de punto de entrada nativo no se generará.

Al tomar la dirección de una función nativa si **__clrcall** no se especifica, el compilador usa el punto de entrada nativo. **__clrcall** indica que se administra la función y no hay ninguna necesidad de realizar la transición de administrado a código nativo. En ese caso, el compilador usa el punto de entrada administrado.

Cuando `/clr` (no `/clr:pure` o `/clr:safe`) se usa y **__clrcall** no es usa, tomar la dirección de una función siempre devuelve la dirección de la función de punto de entrada nativo. Cuando **__clrcall** es usado, la función de punto de entrada nativo no se crea, por lo que obtiene la dirección de la función administrada, no una función de código thunk de punto de entrada. Para obtener más información, consulte [doble thunk](../dotnet/double-thunking-cpp.md). El **/CLR: pure** y **/CLR: safe** opciones del compilador están en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

[/ CLR (common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md) implica que todas las funciones y punteros de función son **__clrcall** y el compilador no permitirá que una función dentro del compilando esté marcada como algo distinto de **__clrcall**. Cuando **/CLR: pure** sirve, **__clrcall** solo se puede especificar en punteros de función y declaraciones externas.

Se puede llamar directamente a **__clrcall** funciones desde código C++ existente que se ha compilado con **/CLR** siempre que esa función tenga una implementación MSIL. **__clrcall** funciones no se puede llamar directamente desde funciones con asm insertado y llamar a intrínsecas de CPU, por ejemplo, incluso si esas funciones se compilan con `/clr`.

**__clrcall** punteros de función solo están diseñados para usarse en el dominio de aplicación en el que se crearon.  En lugar de pasar **__clrcall** punteros de función entre dominios de aplicación, use <xref:System.CrossAppDomainDelegate>. Para obtener más información, consulte [dominios de aplicación y Visual C++](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Ejemplo

Tenga en cuenta que cuando se declara una función con **__clrcall**, se generará código cuando sea necesario; por ejemplo, cuando se llama a función.

```cpp
// clrcall2.cpp
// compile with: /clr
using namespace System;
int __clrcall Func1() {
   Console::WriteLine("in Func1");
   return 0;
}

// Func1 hasn't been used at this point (code has not been generated),
// so runtime returns the adddress of a stub to the function
int (__clrcall *pf)() = &Func1;

// code calls the function, code generated at difference address
int i = pf();   // comment this line and comparison will pass

int main() {
   if (&Func1 == pf)
      Console::WriteLine("&Func1 == pf, comparison succeeds");
   else
      Console::WriteLine("&Func1 != pf, comparison fails");

   // even though comparison fails, stub and function call are correct
   pf();
   Func1();
}
```

```Output
in Func1
&Func1 != pf, comparison fails
in Func1
in Func1
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra que se puede definir un puntero de función, de modo que se declare que el puntero de función solo se invoque desde código administrado. Esto permite que el compilador llame directamente a la función administrada y evite el punto de entrada nativo (problema de doble código thunk).

```cpp
// clrcall3.cpp
// compile with: /clr
void Test() {
   System::Console::WriteLine("in Test");
}

int main() {
   void (*pTest)() = &Test;
   (*pTest)();

   void (__clrcall *pTest2)() = &Test;
   (*pTest2)();
}
```

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)<br/>
[Palabras clave](../cpp/keywords-cpp.md)
