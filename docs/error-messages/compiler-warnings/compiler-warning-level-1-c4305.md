---
title: Compilador advertencia (nivel 1) C4305 | Documentos de Microsoft
ms.custom: 
ms.date: 1/17/2018
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4305
dev_langs:
- C++
helpviewer_keywords:
- C4305
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 8fe4b2b420c44584fdd5b4d48b4264bbc7a51bee
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="compiler-warning-level-1-c4305"></a>Advertencia del compilador (nivel 1) C4305

> '*contexto*': truncamiento de '*type1*'to'*type2*'  

## <a name="remarks"></a>Comentarios

Esta advertencia se emite cuando un valor se convierte en un tipo más pequeño en una inicialización o como un argumento de constructor, lo que causará una pérdida de información.

## <a name="example"></a>Ejemplo

Este ejemplo muestra dos formas, es posible que vea esta advertencia:

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

Para corregir este problema, inicialice mediante un valor del tipo correcto o use una conversión explícita al tipo correcto. Por ejemplo, use un **float** literal como 2.71828f en lugar de un **doble** (el tipo predeterminado para los literales de punto flotante) para inicializar una **float** variable, o para pasar a un constructor que toma un **float** argumento.
