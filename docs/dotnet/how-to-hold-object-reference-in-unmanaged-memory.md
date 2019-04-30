---
title: Procedimiento Mantener una referencia de objeto en memoria no administrada
ms.custom: get-started-article
ms.date: 11/04/2016
helpviewer_keywords:
- object references, in native functions
- objects [C++], reference in native functions
- references, to objects in native functions
- gcroot keyword [C++], object reference in native function
ms.assetid: a61eb8ce-3982-477d-8d3d-2173fd57166d
ms.openlocfilehash: 0d8dc341d1fe2c61eba098abec9258a2c6dade79
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62387297"
---
# <a name="how-to-hold-object-reference-in-unmanaged-memory"></a>Procedimiento Mantener una referencia de objeto en memoria no administrada

Puede usar gcroot.h, que encapsula <xref:System.Runtime.InteropServices.GCHandle>, para mantener una referencia de objeto CLR en memoria no administrada. Como alternativa, puede usar `GCHandle` directamente.

## <a name="example"></a>Ejemplo

```
// hold_object_reference.cpp
// compile with: /clr
#include "gcroot.h"
using namespace System;

#pragma managed
class StringWrapper {

private:
   gcroot<String ^ > x;

public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      x = str;
   }

   void PrintString() {
      String ^ targetStr = x;
      Console::WriteLine("StringWrapper::x == {0}", targetStr);
   }
};
#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::x == ManagedString
```

## <a name="example"></a>Ejemplo

`GCHandle` Proporciona un medio para mantener una referencia de objeto administrado en memoria no administrada.  Usa el <xref:System.Runtime.InteropServices.GCHandle.Alloc%2A> método para crear un identificador opaco a un objeto administrado y <xref:System.Runtime.InteropServices.GCHandle.Free%2A> para liberarlo. Además, el <xref:System.Runtime.InteropServices.GCHandle.Target%2A> método le permite obtener la referencia al objeto desde el controlador en código administrado.

```
// hold_object_reference_2.cpp
// compile with: /clr
using namespace System;
using namespace System::Runtime::InteropServices;

#pragma managed
class StringWrapper {
   IntPtr m_handle;
public:
   StringWrapper() {
      String ^ str = gcnew String("ManagedString");
      m_handle = static_cast<IntPtr>(GCHandle::Alloc(str));
   }
   ~StringWrapper() {
      static_cast<GCHandle>(m_handle).Free();
   }

   void PrintString() {
      String ^ targetStr = safe_cast< String ^ >(static_cast<GCHandle>(m_handle).Target);
      Console::WriteLine("StringWrapper::m_handle == {0}", targetStr);
   }
};

#pragma unmanaged
int main() {
   StringWrapper s;
   s.PrintString();
}
```

```Output
StringWrapper::m_handle == ManagedString
```

## <a name="see-also"></a>Vea también

[Usar la interoperabilidad de C++ (PInvoke implícito)](../dotnet/using-cpp-interop-implicit-pinvoke.md)
