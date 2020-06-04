---
title: __clrcall
ms.date: 11/04/2016
f1_keywords:
- __clrcall_cpp
helpviewer_keywords:
- __clrcall keyword [C++]
ms.assetid: 92096695-683a-40ed-bf65-0c8443572152
ms.openlocfilehash: 6eb1a05eaf6669daa4cb7142ff16a57f7caf39cd
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857611"
---
# <a name="__clrcall"></a>__clrcall

Especifica que solo se puede llamar a una función desde código administrado.  Use **__clrcall** para todas las funciones virtuales a las que solo se llamará desde el código administrado. Sin embargo esta convención de llamada no se puede utilizar para las funciones a las que llamará desde código nativo. El modificador **__clrcall** es específico de Microsoft.

Use **__clrcall** para mejorar el rendimiento al llamar desde una función administrada a una función administrada virtual o desde una función administrada a una función administrada a través de un puntero.

Los puntos de entrada son funciones independientes generadas por el compilador. Si una función tiene puntos de entrada nativos y administrados, uno de ellos será la función real con la implementación de la función. La otra función será una función independiente (un código thunk) que llama a la función real y deja que Common Language Runtime realice PInvoke. Al marcar una función como **__clrcall**, indica que la implementación de la función debe ser MSIL y que no se generará la función de punto de entrada nativo.

Cuando se toma la dirección de una función nativa si no se especifica **__clrcall** , el compilador usa el punto de entrada nativo. **__clrcall** indica que la función está administrada y no es necesario pasar por la transición de administrado a nativo. En ese caso, el compilador usa el punto de entrada administrado.

Cuando se usa `/clr` (no `/clr:pure` o `/clr:safe`) y no se utiliza **__clrcall** , la toma de la dirección de una función siempre devuelve la dirección de la función de punto de entrada nativo. Cuando se utiliza **__clrcall** , no se crea la función de punto de entrada nativo, por lo que se obtiene la dirección de la función administrada, no una función de thunk de punto de entrada. Para obtener más información, vea [double thunk](../dotnet/double-thunking-cpp.md). Las opciones del compilador **/clr: Pure** y **/clr: Safe** están en desuso en Visual Studio 2015 y no se admiten en Visual Studio 2017.

[/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md) implica que todas las funciones y punteros de función son **__clrcall** y el compilador no permitirá que una función dentro de la operación de compilación se marque como algo que no sea **__clrcall**. Cuando se usa **/clr: Pure** , solo se puede especificar **__clrcall** en punteros a función y declaraciones externas.

Puede llamar directamente a las funciones de __clrcall C++ desde el código existente que se compiló mediante **/CLR** siempre que esa función tenga una implementación de MSIL. no se puede llamar a **__clrcall** funciones directamente desde funciones que tienen ASM en línea y llamar a intrinisics específicos de la CPU, por ejemplo, incluso si esas funciones se compilan con `/clr`.

**__clrcall** los punteros de función solo están diseñados para usarse en el dominio de aplicación en el que se crearon.  En lugar de pasar **__clrcall** punteros de función entre dominios de aplicación, use <xref:System.CrossAppDomainDelegate>. Para obtener más información, consulte [dominios de aplicación C++y objetos visuales ](../dotnet/application-domains-and-visual-cpp.md).

## <a name="example"></a>Ejemplo

Tenga en cuenta que cuando una función se declara con **__clrcall**, se generará código cuando sea necesario. por ejemplo, cuando se llama a la función.

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
