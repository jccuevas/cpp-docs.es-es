---
title: Advertencia del compilador (nivel 1) C4186
ms.date: 11/04/2016
f1_keywords:
- C4186
helpviewer_keywords:
- C4186
ms.assetid: caf3f7d8-f305-426b-8d4e-2b96f5c269ea
ms.openlocfilehash: fa5f0c3d3d409384b7cdc3c8a9cbe884732cbf8c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50646581"
---
# <a name="compiler-warning-level-1-c4186"></a>Advertencia del compilador (nivel 1) C4186

\#importación de atributo 'attribute' requiere argumentos count; pasa por alto

Un atributo `#import` tiene un número incorrecto de argumentos.

## <a name="example"></a>Ejemplo

```
// C4186.cpp
// compile with: /W1 /c
#import "stdole2.tlb" no_namespace("abc") rename("a","b","c")  // C4186
```

El atributo `no_namespace` no toma ningún argumento. El atributo **rename** solo toma dos argumentos.