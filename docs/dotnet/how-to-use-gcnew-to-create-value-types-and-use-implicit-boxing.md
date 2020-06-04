---
title: 'Cómo: Usar gcnew para crear tipos de valor y usar la conversión boxing implícita'
ms.date: 11/04/2016
helpviewer_keywords:
- gcnew keyword [C++], creating value types
- boxing, implicit
- value types, creating
ms.assetid: ceb48841-d6bd-47be-a167-57f44c961603
ms.openlocfilehash: 891704d24ca7a7bf8724c8e57faa2aef20a7f982
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "79544878"
---
# <a name="how-to-use-gcnew-to-create-value-types-and-use-implicit-boxing"></a>Cómo: Usar gcnew para crear tipos de valor y usar la conversión boxing implícita

El uso de [gcnew](../extensions/ref-new-gcnew-cpp-component-extensions.md) en un tipo de valor creará un tipo de valor con conversión boxing, que se puede colocar después en el montón administrado y de recolección de elementos no utilizados.

## <a name="example"></a>Ejemplo

```cpp
// vcmcppv2_explicit_boxing4.cpp
// compile with: /clr
public value class V {
public:
   int m_i;
   V(int i) : m_i(i) {}
};

public ref struct TC {
   void do_test(V^ v) {
      if (v != nullptr)
         ;
      else
         ;
   }
};

int main() {
   V^ v = gcnew V(42);
   TC^ tc = gcnew TC;
   tc->do_test(v);
}
```

## <a name="see-also"></a>Consulte también

[Conversión boxing](../extensions/boxing-cpp-component-extensions.md)
