---
title: Operador de referencia de seguimiento (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- '%'
helpviewer_keywords:
- tracking references
- '% tracking reference [C++]'
ms.assetid: 142a7269-ab69-4b54-a6d7-833bef06228f
ms.openlocfilehash: ab1b11d3f8d3416a6e9ed345085d63ce86d56010
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181790"
---
# <a name="tracking-reference-operator-ccli-and-ccx"></a>Operador de referencia de seguimiento (C++/CLI y C++/CX)

Una *referencia de seguimiento* (`%`) se comporta como una referencia de C++ normal (`&`) excepto en que, cuando se asigna un objeto a una referencia de seguimiento, se incrementa el recuento de referencias del objeto.

## <a name="all-platforms"></a>Todas las plataformas

Una referencia de seguimiento tiene las siguientes características.

- La asignación de un objeto a una referencia de seguimiento hace que el recuento de referencias del objeto se incremente.

- Una referencia nativa (`&`) es el resultado de deshacer una referencia de `*`. Una referencia de seguimiento (`%`) es el resultado de deshacer una referencia de `^`. Siempre que tenga `%` para un objeto, el objeto permanecerá activo en memoria.

- Se utiliza el operador de acceso a miembros de punto (`.`) para tener acceso a un miembro del objeto.

- Las referencias de seguimiento son válidas para identificadores y tipos de valor (por ejemplo, `String^`).

- A una referencia de seguimiento no se le puede asignar un valor null o **nullptr**. Una referencia de seguimiento se puede reasignar a otro objeto válido tantas veces como sea necesario.

- Una referencia de seguimiento no se puede utilizar como un operador de toma de direcciones unario.

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Una referencia de seguimiento se comporta como una referencia de C++ estándar, salvo que un % se cuenta como referencia. El siguiente fragmento de código muestra cómo convertir entre tipos % y ^:

```cpp
Foo^ spFoo = ref new Foo();
Foo% srFoo = *spFoo;
Foo^ spFoo2 = %srFoo;
```

En el siguiente ejemplo se muestra cómo pasar un ^ a una función que toma un %.

```cpp
ref class Foo sealed {};

    // internal or private
    void UseFooHelper(Foo% f)
    {
        auto x = %f;
    }

    // public method on ABI boundary
    void UseFoo(Foo^ f)
    {
        if (f != nullptr) { UseFooHelper(*f); }
    }
```

## <a name="common-language-runtime"></a>Common Language Runtime

En C++/CLI puede usar una referencia de seguimiento a un identificador cuando enlaza a un objeto de un tipo CLR en el montón de recolección de elementos no utilizados.

En CLR, el valor de una variable de referencia de seguimiento se actualiza de manera automática siempre que el recolector de elementos no utilizados mueve el objeto de referencia.

Una referencia de seguimiento solo se puede declarar en la pila. Una referencia de seguimiento no puede ser un miembro de una clase.

No es posible tener una referencia de C++ nativa a un objeto en el montón de recolección de elementos no utilizados.

Para obtener más información sobre las referencias de seguimiento en C++/CLI, vea:

- [Cómo: Usar referencias de seguimiento en C++/CLI](../dotnet/how-to-use-tracking-references-in-cpp-cli.md)

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente para C++/CLI se muestra cómo usar una referencia de seguimiento con tipos administrados y nativos.

```cpp
// tracking_reference_1.cpp
// compile with: /clr
ref class MyClass {
public:
   int i;
};

value struct MyStruct {
   int k;
};

int main() {
   MyClass ^ x = ref new MyClass;
   MyClass ^% y = x;   // tracking reference handle to reference object

   int %ti = x->i;   // tracking reference to member of reference type

   int j = 0;
   int %tj = j;   // tracking reference to object on the stack

   int * pi = new int[2];
   int % ti2 = pi[0];   // tracking reference to object on native heap

   int *% tpi = pi;   // tracking reference to native pointer

   MyStruct ^ x2 = ref new MyStruct;
   MyStruct ^% y2 = x2;   // tracking reference to value object

   MyStruct z;
   int %tk = z.k;   // tracking reference to member of value type

   delete[] pi;
}
```

En el ejemplo siguiente para C++/CLI se muestra la manera de enlazar una referencia de seguimiento a una matriz.

```cpp
// tracking_reference_2.cpp
// compile with: /clr
using namespace System;

int main() {
   array<int> ^ a = ref new array<Int32>(5);
   a[0] = 21;
   Console::WriteLine(a[0]);
   array<int> ^% arr = a;
   arr[0] = 222;
   Console::WriteLine(a[0]);
}
```

```Output
21
222
```
