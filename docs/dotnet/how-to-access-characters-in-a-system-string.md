---
title: 'Cómo: Tener acceso a caracteres en un objeto System::String'
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- characters [C++], accessing in System::String
- examples [C++], strings
- strings [C++], accessing characters
ms.assetid: cfc89756-aef3-4988-907e-fb236dcb7087
ms.openlocfilehash: 3c44c5e7651bb1c5b4c28654b896cbe64bd5bec7
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79545346"
---
# <a name="how-to-access-characters-in-a-systemstring"></a>Cómo: Tener acceso a caracteres en un objeto System::String

Puede tener acceso a los caracteres de un objeto <xref:System.String> para las llamadas de alto rendimiento a funciones no administradas que toman cadenas de `wchar_t*`. El método produce un puntero interior al primer carácter del objeto <xref:System.String>. Este puntero se puede manipular directamente o anclar y pasar a una función que espera una cadena de `wchar_t` normal.

## <a name="example"></a>Ejemplo

`PtrToStringChars` devuelve un <xref:System.Char>, que es un puntero interior (también conocido como `byref`). Como tal, está sujeta a la recolección de elementos no utilizados. No tiene que anclar este puntero a menos que vaya a pasarlo a una función nativa.

Observe el código siguiente.  El anclaje no es necesario porque `ppchar` es un puntero interior y, si el recolector de elementos no utilizados mueve la cadena a la que apunta, también actualizará `ppchar`. Sin un [pin_ptr (C++/CLI)](../extensions/pin-ptr-cpp-cli.md), el código funcionará y no se producirá la posible disminución del rendimiento causada por el anclaje.

Si pasa `ppchar` a una función nativa, debe ser un puntero anclado; el recolector de elementos no utilizados no podrá actualizar ningún puntero en el marco de pila no administrado.

```cpp
// PtrToStringChars.cpp
// compile with: /clr
#include<vcclr.h>
using namespace System;

int main() {
   String ^ mystring = "abcdefg";

   interior_ptr<const Char> ppchar = PtrToStringChars( mystring );

   for ( ; *ppchar != L'\0'; ++ppchar )
      Console::Write(*ppchar);
}
```

```Output
abcdefg
```

## <a name="example"></a>Ejemplo

Este ejemplo muestra dónde se necesita el anclaje.

```cpp
// PtrToStringChars_2.cpp
// compile with: /clr
#include <string.h>
#include <vcclr.h>
// using namespace System;

size_t getlen(System::String ^ s) {
   // Since this is an outside string, we want to be secure.
   // To be secure, we need a maximum size.
   size_t maxsize = 256;
   // make sure it doesn't move during the unmanaged call
   pin_ptr<const wchar_t> pinchars = PtrToStringChars(s);
   return wcsnlen(pinchars, maxsize);
};

int main() {
   System::Console::WriteLine(getlen("testing"));
}
```

```Output
7
```

## <a name="example"></a>Ejemplo

Un puntero interior tiene todas las propiedades de un puntero C++ nativo. Por ejemplo, puede utilizarlo para recorrer una estructura de datos vinculada y realizar inserciones y eliminaciones mediante un solo puntero:

```cpp
// PtrToStringChars_3.cpp
// compile with: /clr /LD
using namespace System;
ref struct ListNode {
   Int32 elem;
   ListNode ^ Next;
};

void deleteNode( ListNode ^ list, Int32 e ) {
   interior_ptr<ListNode ^> ptrToNext = &list;
   while (*ptrToNext != nullptr) {
      if ( (*ptrToNext) -> elem == e )
         *ptrToNext = (*ptrToNext) -> Next;   // delete node
      else
         ptrToNext = &(*ptrToNext) -> Next;   // move to next node
   }
}
```

## <a name="see-also"></a>Consulte también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
