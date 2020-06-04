---
title: Advertencia del compilador (nivel 1) C4399
ms.date: 11/04/2016
f1_keywords:
- C4399
helpviewer_keywords:
- C4399
ms.assetid: f58d9ba7-71a0-4c3b-b26f-f946dda8af30
ms.openlocfilehash: a556fbffad41d04b3eb0ea1acfd5e8739ddd5b68
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80186808"
---
# <a name="compiler-warning-level-1-c4399"></a>Advertencia del compilador (nivel 1) C4399

> '*Symbol*': el símbolo por proceso no se debe marcar con __declspec (dllimport) cuando se compila con/CLR: Pure

## <a name="remarks"></a>Observaciones

La opción del compilador **/clr: Pure** ha quedado en desuso en visual Studio 2015 y no se admite en visual Studio 2017.

Los datos de una imagen nativa o de una imagen con construcciones nativas y CLR no se pueden importar en una imagen pura. Para resolver esta advertencia, compile con **/CLR** (no **/clr: Pure**) o elimine `__declspec(dllimport)`.

## <a name="example"></a>Ejemplo

En el ejemplo siguiente se genera C4399.

```cpp
// C4399.cpp
// compile with: /clr:pure /doc /W1 /c
__declspec(dllimport) __declspec(process) extern const int i;   // C4399
```
