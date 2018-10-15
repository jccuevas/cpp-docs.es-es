---
title: ref new, gcnew (C++ / c++ / CLI y c++ / CX) | Documentos de Microsoft
ms.custom: ''
ms.date: 10/12/2018
ms.technology:
- cpp-windows
ms.topic: reference
f1_keywords:
- gcnew
- ref new
- gcnew_cpp
dev_langs:
- C++
helpviewer_keywords:
- ref new keyword (C++)
- gcnew keyword [C++]
ms.assetid: 388a62da-c2df-4a94-a9a2-205b53e577da
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: f5a10278957e6a89b52e744f8f0dd78b475f7730
ms.sourcegitcommit: 3f4e92266737ecb70507871e87dc8e2965ad7e04
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2018
ms.locfileid: "49328316"
---
# <a name="ref-new-gcnew--ccli-and-ccx"></a>ref new, gcnew (C++ / c++ / CLI y c++ / CX)

El **referencia nuevos** palabra clave agregada asigna una instancia de un tipo que se recolecta cuando el objeto deja de estar accesible y que devuelve un identificador ([^](../windows/handle-to-object-operator-hat-cpp-component-extensions.md)) al objeto asignado.

## <a name="all-runtimes"></a>Todos los runtimes

Memoria para una instancia de un tipo que está asignada por **referencia nuevos** se desasigna automáticamente.

Un **referencia nuevos** operación produce `OutOfMemoryException` si no puede asignar memoria.

Para obtener más información acerca de cómo asigna y desasigna memoria para tipos nativos de C++, vea [el nuevo y eliminar operadores](../cpp/new-and-delete-operators.md).

## <a name="windows-runtime"></a>Windows en tiempo de ejecución

Use **referencia nuevos** asignar memoria para objetos de Windows Runtime cuya duración desee administrar automáticamente. El objeto se desasigna automáticamente cuando su recuento de referencias llega a cero, lo que sucede después de que la última copia de la referencia salga del ámbito. Para obtener más información, consulte [clases y structs Ref](../cppcx/ref-classes-and-structs-c-cx.md).

### <a name="requirements"></a>Requisitos

Opción del compilador: `/ZW`

## <a name="common-language-runtime"></a>Common Language Runtime

Se asigna memoria para un tipo administrado (tipo de valor o referencia) por **gcnew**y se desasigna mediante la recolección de elementos.

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

En el ejemplo siguiente se usa **gcnew** para crear un tipo de valor con conversión boxing para su uso como un tipo de referencia.

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

## <a name="see-also"></a>Vea también

[Extensiones de componentes de .NET y UWP](../windows/component-extensions-for-runtime-platforms.md)