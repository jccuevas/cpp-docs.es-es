---
title: 'Cómo: serializar cadenas Unicode mediante la interoperabilidad de C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: f666e52b604e4713f02cb14744ac12a0407366a3
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544890"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Cómo: serializar cadenas Unicode mediante la interoperabilidad de C++

En este tema se muestra una faceta C++ de interoperabilidad visual. Para obtener más información, [vea C++ usar Interop (implicit PInvoke)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

En los siguientes ejemplos de código se usan las directivas de #pragma [administradas y no administradas](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero estas funciones interoperan de la misma manera si se definen en archivos independientes. No es necesario compilar los archivos que contienen solo funciones no administradas con [/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

En este tema se muestra cómo se pueden pasar cadenas Unicode de una función administrada a una función no administrada y viceversa. Para interoperar con otros tipos de cadenas, vea los temas siguientes:

- [Cómo: Serializar cadenas ANSI mediante la interoperabilidad de C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Cómo: Serializar cadenas COM mediante la interoperabilidad de C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>Ejemplo

Para pasar una cadena Unicode de una función administrada a una función no administrada, se puede usar la función PtrToStringChars (declarada en vcclr. h) para tener acceso a en la memoria donde se almacena la cadena administrada. Dado que esta dirección se pasará a una función nativa, es importante anclar la memoria con [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) para evitar que los datos de la cadena se reubiquen, en caso de que se produzca un ciclo de recolección de elementos no utilizados mientras se ejecuta la función no administrada.

```cpp
// MarshalUnicode1.cpp
// compile with: /clr
#include <iostream>
#include <stdio.h>
#include <vcclr.h>

using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(const wchar_t* p) {
   printf_s("(native) received '%S'\n", p);
}

#pragma managed

int main() {
   String^ s = gcnew String("test string");
   pin_ptr<const wchar_t> str = PtrToStringChars(s);

   Console::WriteLine("(managed) passing string to native func...");
   NativeTakesAString( str );
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra el cálculo de referencias de datos necesario para tener acceso a una cadena Unicode en una función administrada a la que llama una función no administrada. La función administrada, al recibir la cadena Unicode nativa, la convierte en una cadena administrada mediante el método <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A>.

```cpp
// MarshalUnicode2.cpp
// compile with: /clr
#include <iostream>

using namespace std;
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedStringFunc(wchar_t* s) {
   String^ ms = Marshal::PtrToStringUni((IntPtr)s);
   Console::WriteLine("(managed) received '{0}'", ms);
}

#pragma unmanaged

void NativeProvidesAString() {
   cout << "(unmanaged) calling managed func...\n";
   ManagedStringFunc(L"test string");
}

#pragma managed

int main() {
   NativeProvidesAString();
}
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
