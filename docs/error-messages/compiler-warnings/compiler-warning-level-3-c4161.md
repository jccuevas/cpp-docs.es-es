---
title: Advertencia del compilador (nivel 3) C4161
ms.date: 08/27/2018
f1_keywords:
- C4161
helpviewer_keywords:
- C4161
ms.assetid: 03d3be61-83f1-4009-8310-8758ab67055f
ms.openlocfilehash: e1bbc949c298a7cfb6c3a3a061616db3dc4730f4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555845"
---
# <a name="compiler-warning-level-3-c4161"></a>Advertencia del compilador (nivel 3) C4161

> #<a name="pragma-pragmapop--more-pops-than-pushes"></a>pragma *pragma*(POP...): más elementos POP que Push

## <a name="remarks"></a>Comentarios

Como el código fuente contiene una extracción más que inserciones hay para la pragma *pragma*, es posible que la pila no tenga el comportamiento esperado. Para evitar la advertencia, asegúrese de que el número de extracciones no supera el número de inserciones.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera el error C4161:

```cpp
// C4161.cpp
// compile with: /W3 /LD
#pragma pack(push, id)
#pragma pack(pop, id)
#pragma pack(pop, id)   // C4161, an extra pop

#pragma bss_seg(".my_data1")
int j;

#pragma bss_seg(push, stack1, ".my_data2")
int l;

#pragma bss_seg(pop, stack1)
int m;

#pragma bss_seg(pop, stack1)   // C4161
```