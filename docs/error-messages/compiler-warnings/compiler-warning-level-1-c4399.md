---
title: Advertencia del compilador (nivel 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: 56fe0f314142d873fc02136bc2c3fe65e71f4dda
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50544071"
---
# <a name="compiler-warning-level-1-c4399"></a>Advertencia del compilador (nivel 1) C4399

> '*símbolo*': símbolo por proceso no se debe marcar con __declspec (dllimport) cuando se compila con/CLR: pure

## <a name="remarks"></a>Comentarios

El **/CLR: pure** opción del compilador está en desuso en Visual Studio 2015 y no se admite en Visual Studio 2017.

No se pueden importar datos desde una imagen nativa o una imagen con construcciones nativas y CLR en una imagen pura. Para resolver esta advertencia, compile con **/CLR** (no **/CLR: pure**) o eliminar `__declspec(dllimport)`.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```