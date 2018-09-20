---
title: 'Cómo: serializar punteros a función mediante PInvoke | Microsoft Docs'
ms.custom: get-started-article
ms.date: 11/04/2016
ms.technology:
- cpp-cli
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- data marshaling [C++], callbacks and delegates
- interop [C++], callbacks and delegates
- platform invoke [C++], callbacks and delegates
- marshaling [C++], callbacks and delegates
ms.assetid: dcf396fd-a91d-49c0-ab0b-1ea160668a89
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- dotnet
ms.openlocfilehash: 5246105f8824c3514213a3f7733b731789837403
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46415088"
---
# <a name="how-to-marshal-function-pointers-using-pinvoke"></a>Cómo: serializar punteros a función mediante PInvoke

Este tema explica cómo administrados delegados puede usarse en lugar de punteros a función al interoperar con funciones no administradas mediante las características de .NET Framework P/Invoke. Sin embargo, los programadores de Visual C++ se recomienda utilizar las características de interoperabilidad de C++ en su lugar (cuando sea posible) ya que P/Invoke proporciona pocos informes, de errores de tiempo de compilación no es seguro para el tipo y puede ser tedioso de implementar. Si la API no administrada se empaqueta como un archivo DLL y el código fuente no está disponible, P/Invoke es la única opción. En caso contrario, vea los temas siguientes:

- [Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)

- [Cómo: Serializar devoluciones de llamadas y delegados mediante la interoperabilidad de C++](../dotnet/how-to-marshal-callbacks-and-delegates-by-using-cpp-interop.md)

API no administradas que toman punteros a funciones como argumentos pueden llamarse desde código administrado con un delegado administrado en lugar del puntero de función nativo. El compilador automáticamente calcula las referencias del delegado a funciones no administradas como un puntero de función e inserta el código de transición administrado y no es necesario.

## <a name="example"></a>Ejemplo

El código siguiente consta de un no administrado y un módulo administrado. El módulo no administrado es un archivo DLL que define una función llamada TakesCallback que acepta un puntero de función. Esta dirección se utiliza para ejecutar la función.

El módulo administrado define un delegado que se calculan las referencias al código nativo como un puntero de función y usa el <xref:System.Runtime.InteropServices.DllImportAttribute> atributo para exponer la función TakesCallback nativa del código administrado. En la función principal, una instancia del delegado se crea y pasa a la función TakesCallback. La salida del programa muestra que esta función se ejecute por la función TakesCallback nativa.

La función administrada suprime la recolección de elementos para el delegado administrado impedir la recolección de .NET Framework reubique el delegado mientras se ejecuta la función nativa.

```cpp
// TraditionalDll5.cpp
// compile with: /LD /EHsc
#include <iostream>
#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   /* Declare an unmanaged function type that takes two int arguments
      Note the use of __stdcall for compatibility with managed code */
   typedef int (__stdcall *CALLBACK)(int);
   TRADITIONALDLL_API int TakesCallback(CALLBACK fp, int);
}

int TakesCallback(CALLBACK fp, int n) {
   printf_s("[unmanaged] got callback address, calling it...\n");
   return fp(n);
}
```

```cpp
// MarshalDelegate.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

public delegate int GetTheAnswerDelegate(int);
public value struct TraditionalDLL {
   [DllImport("TraditionalDLL5.dll")]
   static public int TakesCallback(GetTheAnswerDelegate^ pfn, int n);
};

int GetNumber(int n) {
   Console::WriteLine("[managed] callback!");
   static int x = 0;
   ++x;
   return x + n;
}

int main() {
   GetTheAnswerDelegate^ fp = gcnew GetTheAnswerDelegate(GetNumber);
   pin_ptr<GetTheAnswerDelegate^> pp = &fp;
   Console::WriteLine("[managed] sending delegate as callback...");

   int answer = TraditionalDLL::TakesCallback(fp, 42);
}
```

Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado mediante la tradicional #include (directiva). De hecho, se tiene acceso a la DLL en tiempo de ejecución, por lo que los problemas con las funciones que se importan con <xref:System.Runtime.InteropServices.DllImportAttribute> no se detectarán en tiempo de compilación.

## <a name="see-also"></a>Vea también

[Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)