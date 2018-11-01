---
title: 'Cómo: Declarar punteros anclados y tipos de valor'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: ed7835e3ab6ccda724ccb6c0d7cf5dab8dd4d342
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50660868"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>Cómo: Declarar punteros anclados y tipos de valor

Un tipo de valor puede ser implícitamente la conversión boxing. A continuación, puede declarar un puntero anclado para el objeto de tipo de valor propio y usar un **pin_ptr** al tipo de valor con conversión boxing.

## <a name="example"></a>Ejemplo

### <a name="code"></a>Código

```cpp
// pin_ptr_value.cpp
// compile with: /clr
value struct V {
   int i;
};

int main() {
   V ^ v = gcnew V;   // imnplicit boxing
   v->i=8;
   System::Console::WriteLine(v->i);
   pin_ptr<V> mv = &*v;
   mv->i = 7;
   System::Console::WriteLine(v->i);
   System::Console::WriteLine(mv->i);
}
```

```Output
8
7
7
```

## <a name="see-also"></a>Vea también

[pin_ptr (C++/CLI)](../windows/pin-ptr-cpp-cli.md)