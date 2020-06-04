---
title: ref new, gcnew (C++/CLI y C++/CX)
ms.date: 10/12/2018
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
ms.openlocfilehash: f7269a62d7899df4eb89f6dd9487310c0fda0b4d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181816"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new, gcnew (C++/CLI y C++/CX)

La palabra clave agregada **ref new** asigna una instancia de un tipo que se recolecta como elemento no utilizado cuando el objeto deja de estar accesible y que devuelve un identificador ([^](handle-to-object-operator-hat-cpp-component-extensions.md)) al objeto asignado.

## <a name="all-runtimes"></a>Todos los runtimes

La memoria para una instancia de un tipo que se asigna mediante **ref new** se desasigna automáticamente.

Una operación **ref new** inicia `OutOfMemoryException` si no puede asignar memoria.

Para obtener más información sobre la manera en que se asigna y se desasigna memoria para tipos nativos de C++, consulte [los operadores new y delete](../cpp/new-and-delete-operators.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Use **ref new** para asignar memoria para objetos de Windows Runtime cuya duración desee administrar automáticamente. El objeto se desasigna automáticamente cuando su recuento de referencias llega a cero, lo que sucede después de que la última copia de la referencia salga del ámbito. Para obtener más información, consulte el artículo sobre [las clases de referencia y structs](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

La memoria para un tipo administrado (tipo de valor o referencia) se asigna mediante **gcnew** y se desasigna mediante la colección de elementos no utilizados.

### <a name="requirements"></a>Requisitos

Opción del compilador: `/clr`

### <a name="examples"></a>Ejemplos

En el ejemplo siguiente se usa **gcnew** para asignar un objeto de mensaje.

```cpp
// mcppv2_gcnew_1.cpp
// compile with: /clr
ref struct Message {
   System::String^ sender;
   System::String^ receiver;
   System::String^ data;
};

int main() {
   Message^ h_Message  = gcnew Message;
  //...
}
```

En el ejemplo siguiente se usa **gcnew** para crear un tipo de valor con la conversión boxing aplicada para usarlo como tipo de referencia.

```cpp
// example2.cpp : main project file.
// compile with /clr
using namespace System;
value class Boxed {
    public:
        int i;
};
int main()
{
    Boxed^ y = gcnew Boxed;
    y->i = 32;
    Console::WriteLine(y->i);
    return 0;
}
```

```Output
32
```

## <a name="see-also"></a>Consulte también

[Extensiones de componentes de .NET y UWP](component-extensions-for-runtime-platforms.md)
