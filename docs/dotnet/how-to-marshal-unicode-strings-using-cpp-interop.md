---
title: Procedimiento Serializar cadenas Unicode mediante la interoperabilidad de C++
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- Unicode, marshaling strings
ms.assetid: 96c2141d-6c5d-43ef-a1aa-5785afb9a9aa
ms.openlocfilehash: 37b56834e000cff686557730252f3d425f642772
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400557"
---
# <a name="how-to-marshal-unicode-strings-using-c-interop"></a>Procedimiento Serializar cadenas Unicode mediante la interoperabilidad de C++

En este tema se muestra un aspecto de la interoperabilidad de Visual C++. Para obtener más información, consulte [utilizando interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md).

Uso de ejemplos de código siguiente el [managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas #pragma para implementar administrados y las funciones en el mismo archivo, pero estas funciones interoperan de la misma manera, si se definen en archivos independientes. No es necesario que los archivos que contienen solo las funciones no administradas se compilan con [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

Este tema muestra cómo las cadenas de Unicode pueden ser pase de una a una función no administrada y viceversa. Para interoperar con otros tipos de cadenas, vea los temas siguientes:

- [Cómo: Serializar cadenas ANSI mediante la interoperabilidad de C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

- [Cómo: Serializar cadenas COM mediante la interoperabilidad de C++](../dotnet/how-to-marshal-com-strings-using-cpp-interop.md)

## <a name="example"></a>Ejemplo

Para pasar una cadena Unicode de administrado a una función no administrada, se puede usar la función PtrToStringChars (declarada en Vcclr.h) para el acceso en la memoria donde se almacena la cadena administrada. Dado que esta dirección se pasará a una función nativa, es importante que la memoria se anclado con [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) para evitar que los datos de cadena que se ha reubicado, un ciclo de recopilación de elementos no utilizados tendrá lugar mientras el ejecuta la función no administrada.

```
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

El ejemplo siguiente muestra el cálculo de referencias de datos necesarios para tener acceso a una cadena Unicode en una función administrada llamada a una función no administrada. La función administrada, al recibir la cadena Unicode nativa, lo convierte en una cadena administrada mediante el <xref:System.Runtime.InteropServices.Marshal.PtrToStringUni%2A> método.

```
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

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
