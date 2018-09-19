---
title: Compilador advertencia (nivel 1) C4305 | Microsoft Docs
ms.custom: ''
ms.date: 1/17/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 88ae0fb38b7e6af14525906e90486a68ce22ee56
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46086829"
---
# <a name="compiler-warning-level-1-c4305"></a>Advertencia del compilador (nivel 1) C4305

> '*contexto*': truncamiento de '*type1*'para'*type2*'

## <a name="remarks"></a>Comentarios

Esta advertencia se emite cuando un valor se convierte en un tipo más pequeño en una inicialización o como un argumento de constructor, lo que produce una pérdida de información.

## <a name="example"></a>Ejemplo

Este ejemplo muestra dos maneras puede aparecer esta advertencia:

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

Para corregir este problema, inicializar con un valor del tipo correcto, o usar una conversión explícita al tipo correcto. Por ejemplo, use un **float** literal como 2.71828f en lugar de un **doble** (el tipo de valor predeterminado para los literales de punto flotante) para inicializar un **float** variable, o pasar a un constructor que toma un **float** argumento.
