---
title: Procedimiento Serializar cadenas COM mediante la interoperabilidad de C++
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- interop [C++], strings
- marshaling [C++], strings
- C++ Interop, strings
- data marshaling [C++], strings
- COM [C++], marshaling strings
ms.assetid: 06590759-bf99-4e34-a3a9-4527ea592cc2
ms.openlocfilehash: e86cf0b3e57eda9a0f4fa5fe2337d0c42de5669f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62325486"
---
# <a name="how-to-marshal-com-strings-using-c-interop"></a>Procedimiento Serializar cadenas COM mediante la interoperabilidad de C++

Este tema muestra cómo puede ser una cadena BSTR (el formato de cadena básicas preferido en programación COM) pase de una a una función no administrada y viceversa. Para interoperar con otros tipos de cadenas, vea los temas siguientes:

- [Cómo: Serializar cadenas Unicode mediante la interoperabilidad de C++](../dotnet/how-to-marshal-unicode-strings-using-cpp-interop.md)

- [Cómo: Serializar cadenas ANSI mediante la interoperabilidad de C++](../dotnet/how-to-marshal-ansi-strings-using-cpp-interop.md)

Uso de ejemplos de código siguiente el [managed, unmanaged](../preprocessor/managed-unmanaged.md) directivas #pragma para implementar administrados y las funciones en el mismo archivo, pero estas funciones interoperan de la misma manera, si se definen en archivos independientes. No es necesario que los archivos que contienen solo las funciones no administradas se compilan con [/CLR (Common Language Runtime Compilation)](../build/reference/clr-common-language-runtime-compilation.md).

## <a name="example"></a>Ejemplo

El ejemplo siguiente muestra cómo se puede pasar una cadena BSTR (un formato de cadena usado en la programación COM) de administrado a una función no administrada. Realiza la llamada administrada usa función <xref:System.Runtime.InteropServices.Marshal.StringToBSTR%2A> para obtener la dirección de una representación de BSTR del contenido de un objeto .NET System.String. Este puntero se ancla mediante [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) para asegurarse de que su dirección física no se cambia durante un ciclo de recopilación de elementos no utilizados mientras se ejecuta la función no administrada. El recolector de elementos no utilizados se le permite mover la memoria hasta que el [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md) sale del ámbito.

```
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

El ejemplo siguiente muestra cómo se puede pasar una cadena BSTR de un no administrado a una función no administrada. La recepción de función administrada puede usar la cadena como un BSTR o usar <xref:System.Runtime.InteropServices.Marshal.PtrToStringBSTR%2A> para convertirlo en un <xref:System.String> para su uso con otras funciones administradas. Dado que la memoria que representa el BSTR está asignada en el montón no administrado, no hay anclajes es necesario, porque no hay ninguna recolección en el montón no administrado.

```
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

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
