---
title: Procedimiento Sobrecarga de funciones con punteros interiores y punteros nativos (C++/CLI)
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- Functions with interior and native pointers, overloading
ms.assetid: d70df625-4aad-457c-84f5-70a0a290cc1f
ms.openlocfilehash: f84a7efc87985f23b62139f0547c292989537aa6
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "65515730"
---
# <a name="how-to-overload-functions-with-interior-pointers-and-native-pointers-ccli"></a>Procedimiento Sobrecarga de funciones con punteros interiores y punteros nativos (C++/CLI)

Las funciones se pueden sobrecargar en función de si el tipo de parámetro es un puntero interior o un puntero nativo.

> [!IMPORTANT]
> Esta característica del lenguaje es compatible con la opción de compilador `/clr`, pero no con la opción de compilador `/ZW`.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
// interior_ptr_overload.cpp
// compile with: /clr
using namespace System;

// C++ class
struct S {
   int i;
};

// managed class
ref struct G {
   int i;
};

// can update unmanaged storage
void f( int* pi ) {
   *pi = 10;
   Console::WriteLine("in f( int* pi )");
}

// can update managed storage
void f( interior_ptr<int> pi ) {
   *pi = 10;
   Console::WriteLine("in f( interior_ptr<int> pi )");
}

int main() {
   S *pS = new S;   // C++ heap
   G ^pG = gcnew G;   // common language runtime heap
   f( &pS->i );
   f( &pG->i );
};
```

```Output
in f( int* pi )
in f( interior_ptr<int> pi )
```

## <a name="see-also"></a>Vea también

[interior_ptr (C++/CLI)](interior-ptr-cpp-cli.md)