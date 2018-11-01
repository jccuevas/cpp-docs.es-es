---
title: Error del compilador C3213
ms.date: 11/04/2016
f1_keywords:
- C3213
helpviewer_keywords:
- C3213
ms.assetid: 1f079e36-b3e9-40f8-8e95-08eeba3adc82
ms.openlocfilehash: 1b08b0ef5b8fefcfa1dd55ef3a16ee4ef5d027e0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50637819"
---
# <a name="compiler-error-c3213"></a>Error del compilador C3213

La clase base 'base_type' es menos accesible que 'derived_type'

Un tipo que será visible desde un ensamblado debe usar clases base visibles públicamente.

El ejemplo siguiente genera la advertencia C3213:

```
// C3213.cpp
// compile with: /clr
private ref struct privateG {
public:
   int i;
};

public ref struct publicG {
public:
   int i;
};

public ref struct V : public privateG {   // C3213
public:
   int j;
};

public ref struct W: public publicG {   // OK
public:
   int j;
};
```