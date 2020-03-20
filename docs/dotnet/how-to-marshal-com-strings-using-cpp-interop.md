---
title: 'Cómo: Calcular las referencias de cadenas COM mediante la interoperabilidad de C++'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: 8dfdad892261d5ae2d3494734458e1447f8ebd7c
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545232"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Cómo: Calcular las referencias de cadenas COM mediante la interoperabilidad de C++

En este tema se muestra cómo un BSTR (el formato de cadena básico que se favorece en la programación COM) se puede pasar de una función administrada a una función no administrada y viceversa. Para interoperar con otros tipos de cadenas, vea los temas siguientes:

- [Cómo: Serializar cadenas Unicode mediante la interoperabilidad de C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Cómo: Serializar cadenas ANSI mediante la interoperabilidad de C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

En los siguientes ejemplos de código se usan las directivas de #pragma [administradas y no administradas](../preprocessor/managed-unmanaged.md) para implementar funciones administradas y no administradas en el mismo archivo, pero estas funciones interoperan de la misma manera si se definen en archivos independientes. No es necesario compilar los archivos que contienen solo funciones no administradas con [/CLR (compilación de Common Language Runtime)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo se puede pasar un BSTR (un formato de cadena utilizado en la programación COM) desde una función administrada a una función no administrada. La función administrada que realiza la llamada usa <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> para obtener la dirección de una representación BSTR del contenido de un System. String de .NET. Este puntero se ancla mediante [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) para asegurarse de que su dirección física no se cambia durante un ciclo de recolección de elementos no utilizados mientras se ejecuta la función no administrada. El recolector de elementos no utilizados tiene prohibido mover la memoria hasta que el [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) salga del ámbito.

```cpp
// MarshalBSTR1.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma unmanaged

void NativeTakesAString(BSTR bstr) {
   printf_s("%S", bstr);
}

#pragma managed

int main() {
   String^ s = "test string";

   IntPtr ip = Marshal::StringToBSTR(s);
   BSTR bs = static_cast<BSTR>(ip.ToPointer());
   pin_ptr<BSTR> b = &bs;

   NativeTakesAString( bs );
   Marshal::FreeBSTR(ip);
}
```

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se muestra cómo se puede pasar un BSTR desde una función no administrada a una función no administrada. La función administrada de recepción puede usar la cadena en como BSTR o usar <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> para convertirla en un <xref:System.String> para su uso con otras funciones administradas. Dado que la memoria que representa el BSTR se asigna en el montón no administrado, no es necesario el anclaje porque no hay ninguna recolección de elementos no utilizados en el montón no administrado.

```cpp
// MarshalBSTR2.cpp
// compile with: /clr
#define WINVER 0x0502
#define _AFXDLL
#include <afxwin.h>

#include <iostream>
using namespace std;

using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed

void ManagedTakesAString(BSTR bstr) {
   String^ s = Marshal::PtrToStringBSTR(static_cast<IntPtr>(bstr));
   Console::WriteLine("(managed) convered BSTR to String: '{0}'", s);
}

#pragma unmanaged

void UnManagedFunc() {
   BSTR bs = SysAllocString(L"test string");
   printf_s("(unmanaged) passing BSTR to managed func...\n");
   ManagedTakesAString(bs);
}

#pragma managed

int main() {
   UnManagedFunc();
}
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
