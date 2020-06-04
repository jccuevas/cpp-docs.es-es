---
title: Procedimiento Uso de PInvoke de serializar matrices
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- marshaling [C++], arrays
- platform invoke [C++], arrays
- interop [C++], arrays
- data marshaling [C++], arrays
ms.assetid: a1237797-a2da-4df4-984a-6333ed3af406
ms.openlocfilehash: 60b49135928e3dadffc2a3c7a422646d2f3a768d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325447"
---
# <a name="how-to-marshal-arrays-using-pinvoke"></a>Procedimiento Uso de PInvoke de serializar matrices

En este tema se explica cómo funciones nativas que aceptan cadenas de estilo C se pueden llamar mediante el tipo de cadena CLR <xref:System.String> mediante la compatibilidad con la invocación de plataforma de .NET Framework. Los programadores de Visual C++ se recomienda utilizar las características de interoperabilidad de C++ en su lugar (cuando sea posible) ya que P/Invoke proporciona pocos informes, de errores de tiempo de compilación no es seguro para el tipo y puede ser tedioso de implementar. Si la API no administrada se empaqueta como un archivo DLL y el código fuente no está disponible, P/Invoke es la única opción (en caso contrario, consulte [utilizando interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)).

## <a name="example"></a>Ejemplo

Dado que las matrices nativas y administradas se distribuyen de manera diferente en la memoria, correctamente se pasan a través del límite administrado y no requiere conversión o cálculo de referencias. En este tema se muestra cómo se puede pasar una matriz de elementos simple (blitable) a funciones nativas desde código administrado.

Como ocurre con la serialización de datos administrados y no administrados en general, el <xref:System.Runtime.InteropServices.DllImportAttribute> atributo se utiliza para crear un punto de entrada administrado para cada función nativa que se usará. En el caso de las funciones que toman matrices como argumentos, el <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo debe usarse también para especificar al compilador cómo se pueden serializar los datos. En el ejemplo siguiente, la <xref:System.Runtime.InteropServices.UnmanagedType> enumeración se utiliza para indicar que la matriz administrada se convierte en una matriz de estilo C.

El código siguiente consta de un no administrado y un módulo administrado. El módulo no administrado es un archivo DLL que define una función que acepta una matriz de enteros. El segundo módulo es una aplicación de línea de comandos administrada que importa esta función, pero lo define en términos de una matriz administrada y usa el <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para especificar que la matriz se debe convertir en una matriz nativa cuando se le llama.

El módulo administrado se compila con/CLR.

```cpp
// TraditionalDll4.cpp
// compile with: /LD /EHsc
#include <iostream>

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAnArray(int len, int[]);
}

void TakesAnArray(int len, int a[]) {
   printf_s("[unmanaged]\n");
   for (int i=0; i<len; i++)
      printf("%d = %d\n", i, a[i]);
}
```

```cpp
// MarshalBlitArray.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL {
   [DllImport("TraditionalDLL4.dll")]
   static public void TakesAnArray(
   int len,[MarshalAs(UnmanagedType::LPArray)]array<int>^);
};

int main() {
   array<int>^ b = gcnew array<int>(3);
   b[0] = 11;
   b[1] = 33;
   b[2] = 55;
   TraditionalDLL::TakesAnArray(3, b);

   Console::WriteLine("[managed]");
   for (int i=0; i<3; i++)
      Console::WriteLine("{0} = {1}", i, b[i]);
}
```

Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado a través de la tradicional #include (directiva). De hecho, dado que se tiene acceso a la DLL en tiempo de ejecución solo, problemas con las funciones se importan con <xref:System.Runtime.InteropServices.DllImportAttribute> no se detectarán en tiempo de compilación.

## <a name="see-also"></a>Vea también

[Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
