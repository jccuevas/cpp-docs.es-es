---
title: 'Cómo: Declarar punteros anclados y tipos de valor'
ms.date: 10/12/2018
ms.topic: reference
helpviewer_keywords:
- value types, declaring
- pinning pointers
ms.assetid: 57c5ec8a-f85a-48c4-ba8b-a81268bcede0
ms.openlocfilehash: 88ef7e82161703a272a571392fd66e6055371c61
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80181972"
---
# <a name="how-to-declare-pinning-pointers-and-value-types"></a>Cómo: Declarar punteros anclados y tipos de valor

A un tipo de valor se le puede aplicar la conversión boxing de manera implícita. A continuación, puede declarar un puntero anclado al propio objeto de tipo de valor y usar un variable **pin_ptr** para el tipo de valor con conversión boxing.

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

## <a name="see-also"></a>Consulte también

[pin_ptr (C++/CLI)](pin-ptr-cpp-cli.md)
