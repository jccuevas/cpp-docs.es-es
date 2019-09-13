---
title: Advertencia del compilador (nivel 1) C4305
ms.date: 01/17/2018
f1_keywords:
- C4305
helpviewer_keywords:
- C4305
ms.openlocfilehash: dc718e5f7ebe9478ed1bf2a7323db940935cb1d6
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926118"
---
# <a name="compiler-warning-level-1-c4305"></a>Advertencia del compilador (nivel 1) C4305

> '*Context*': truncamiento de '*tipo1*' a '*tipo2*'

## <a name="remarks"></a>Comentarios

Esta advertencia se emite cuando un valor se convierte en un tipo más pequeño en una inicialización o como un argumento de constructor, lo que produce una pérdida de información.

## <a name="example"></a>Ejemplo

En este ejemplo se muestran dos maneras en que se puede ver esta ADVERTENCIA:

```cpp
// C4305.cpp
// Compile by using: cl /EHsc /W4 C4305.cpp

struct item
{
    item(float) {}
};

int main()
{
    float f = 2.71828;          // C4305 'initializing'
    item i(3.14159);            // C4305 'argument'
    return static_cast<int>(f);
}
```

Para corregir este problema, inicialice con un valor del tipo correcto o use una conversión explícita al tipo correcto. Por ejemplo, use un **literal de punto flotante como** 2.71828 f en lugar de un valor **Double** (el tipo predeterminado para los literales de punto flotante) para inicializar una variable **float** o para pasar a un constructor que toma un argumento de **tipo float** .
