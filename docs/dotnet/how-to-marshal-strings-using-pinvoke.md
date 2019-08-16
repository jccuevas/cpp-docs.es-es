---
title: Procedimiento Convertir cadenas utilizando PInvoke
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: f316e33f1711ea0053fb68c0af7e89f90b793e05
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404408"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Procedimiento Convertir cadenas utilizando PInvoke

En este tema se explica cómo funciones nativas que aceptan cadenas de estilo C se pueden llamar mediante la cadena CLR tipo System:: String con el soporte técnico de invocación de plataforma de .NET Framework. Los programadores de Visual C++ se recomienda utilizar las características de interoperabilidad de C++ en su lugar (cuando sea posible) ya que P/Invoke proporciona pocos informes, de errores de tiempo de compilación no es seguro para el tipo y puede ser tedioso de implementar. Si la API no administrada se empaqueta como un archivo DLL y el código fuente no está disponible, P/Invoke es la única opción, pero en caso contrario, consulte [utilizando interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Las cadenas administradas y se distribuyen de manera diferente en la memoria, por lo que el paso de cadenas a partir de administrado a funciones no administradas requiere el <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo para indicar al compilador que inserte los mecanismos de conversión necesario para la serialización de los datos de cadena correcta y segura.

Al igual que con las funciones que usan solo los tipos de datos intrínsecos, <xref:System.Runtime.InteropServices.DllImportAttribute> se utiliza para declarar los puntos de entrada administrado en las funciones nativas, pero para pasar cadenas, en lugar de definir estos puntos de entrada de modo que toman cadenas de estilo C, un identificador para el <xref:System.String> tipo se puede usar en su lugar. Esto indica al compilador que inserte el código que realiza la conversión necesaria. Para cada argumento de función en una función no administrada que toma una cadena, la <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo debería usarse para indicar que se debe serializar el objeto de cadena a la función como una cadena de estilo C nativa.

## <a name="example"></a>Ejemplo

El código siguiente consta de un no administrado y un módulo administrado. El módulo no administrado es un archivo DLL que define una función llamada TakesAString, que acepta una cadena de estilo C ANSI en forma de char *. El módulo administrado es una aplicación de línea de comandos que importa la función TakesAString, pero lo define como teniendo System.String en lugar de un tipo char administrado\*. El <xref:System.Runtime.InteropServices.MarshalAsAttribute> atributo se utiliza para indicar cómo se debe serializar la cadena administrada cuando se llama a TakesAString.

```
// TraditionalDll2.cpp
// compile with: /LD /EHsc
#include <windows.h>
#include <stdio.h>
#include <iostream>

using namespace std;

#define TRADITIONALDLL_EXPORTS
#ifdef TRADITIONALDLL_EXPORTS
#define TRADITIONALDLL_API __declspec(dllexport)
#else
#define TRADITIONALDLL_API __declspec(dllimport)
#endif

extern "C" {
   TRADITIONALDLL_API void TakesAString(char*);
}

void TakesAString(char* p) {
   printf_s("[unmanaged] %s\n", p);
}
```

```
// MarshalString.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

value struct TraditionalDLL
{
   [DllImport("TraditionalDLL2.dll")]
      static public void
      TakesAString([MarshalAs(UnmanagedType::LPStr)]String^);
};

int main() {
   String^ s = gcnew String("sample string");
    Console::WriteLine("[managed] passing managed string to unmanaged function...");
   TraditionalDLL::TakesAString(s);
   Console::WriteLine("[managed] {0}", s);
}
```

Esta técnica hace una copia de la cadena que se construye en el montón no administrado, por lo que no se reflejarán los cambios realizados en la cadena por la función nativa en la copia administrada de la cadena.

Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado a través de la tradicional #include (directiva). De hecho, se tiene acceso a la DLL en tiempo de ejecución, por lo que los problemas con las funciones que se importan con `DllImport` no se detectarán en tiempo de compilación.

## <a name="see-also"></a>Vea también

[Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
