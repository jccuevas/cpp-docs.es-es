---
title: 'Cómo: Calcular las referencias de cadenas mediante PInvoke'
ms.custom: get-started-article
ms.date: 09/09/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- data marshaling [C++], strings
- platform invoke [C++], strings
ms.assetid: bcc75733-7337-4d9b-b1e9-b95a98256088
ms.openlocfilehash: e89177261aa32d34ea392030078d4088ea61e2a5
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545226"
---
# <a name="how-to-marshal-strings-using-pinvoke"></a>Cómo: Calcular las referencias de cadenas mediante PInvoke

En este tema se explica cómo se puede llamar a las funciones nativas que aceptan cadenas de estilo C mediante el tipo de cadena CLR System:: String que usa .NET Framework la compatibilidad con la invocación de plataforma. Se C++ recomienda a los programadores visuales el C++ uso de las características de interoperabilidad en su lugar (cuando sea posible) porque P/Invoke proporciona pocos informes de errores en tiempo de compilación, no tiene seguridad de tipos y puede ser tedioso implementar. Si la API no administrada se empaqueta como un archivo DLL y el código fuente no está disponible, P/Invoke es la única opción; de lo contrario, vea [usar C++ Interop (implicit PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Las cadenas administradas y no administradas se colocan de forma diferente en la memoria, por lo que pasar cadenas de funciones administradas a no administradas requiere el atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> para indicar al compilador que inserte los mecanismos de conversión necesarios para calcular las referencias de los datos de cadena correctamente y de forma segura.

Al igual que con las funciones que solo usan tipos de datos intrínsecos, <xref:System.Runtime.InteropServices.DllImportAttribute> se usa para declarar puntos de entrada administrados en las funciones nativas, pero, para pasar cadenas, en lugar de definir estos puntos de entrada como toma de cadenas de estilo C, se puede utilizar en su lugar un identificador para el tipo de <xref:System.String>. Esto le pedirá al compilador que inserte código que realice la conversión necesaria. Para cada argumento de función de una función no administrada que toma una cadena, se debe usar el atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> para indicar que el objeto de cadena se debe serializar en la función nativa como una cadena de estilo C.

El serializador incluye la llamada a la función no administrada en una rutina de contenedor oculta que fija y copia la cadena administrada en una cadena asignada localmente en el contexto no administrado, que se pasa a continuación a la función no administrada. Cuando la función no administrada devuelve, el contenedor elimina el recurso o, si se encontraba en la pila, se recupera cuando el contenedor sale del ámbito. La función no administrada no es responsable de esta memoria. El código no administrado solo crea y elimina la memoria en el montón configurado por su propio CRT, por lo que nunca hay un problema con el serializador que usa una versión de CRT diferente.

Si la función no administrada devuelve una cadena, ya sea como un valor devuelto o como parámetro out, el serializador lo copia en una nueva cadena administrada y, a continuación, libera la memoria. Para obtener más información, vea [comportamiento del cálculo de referencias predeterminado](/dotnet/framework/interop/default-marshaling-behavior) y [serialización de datos con invocación de plataforma](/dotnet/framework/interop/marshaling-data-with-platform-invoke).

## <a name="example"></a>Ejemplo

El siguiente código consta de un módulo administrado y no administrado. El módulo no administrado es un archivo DLL que define una función llamada TakesAString que acepta una cadena ANSI de estilo C en forma de Char *. El módulo administrado es una aplicación de línea de comandos que importa la función TakesAString, pero la define como si tomara un System. String administrado en lugar de un carácter\*. El atributo <xref:System.Runtime.InteropServices.MarshalAsAttribute> se usa para indicar cómo se deben calcular las referencias de la cadena administrada cuando se llama a TakesAString.

```cpp
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

```cpp
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

Esta técnica hace que se construya una copia de la cadena en el montón no administrado, por lo que los cambios realizados en la cadena por la función nativa no se reflejarán en la copia administrada de la cadena.

Tenga en cuenta que ninguna parte del archivo DLL se expone al código administrado a través de la Directiva de #include tradicional. De hecho, solo se tiene acceso al archivo DLL en tiempo de ejecución, por lo que los problemas con las funciones importadas con `DllImport` no se detectarán en tiempo de compilación.

## <a name="see-also"></a>Consulte también

[Usar un elemento PInvoke explícito en C++ (Atributo DllImport)](../dotnet/using-explicit-pinvoke-in-cpp-dllimport-attribute.md)
