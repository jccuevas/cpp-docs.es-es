---
title: Advertencia del compilador (nivel 4) C4690
ms.date: 07/03/2018
f1_keywords:
- C4690
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
ms.openlocfilehash: c7facdde54b44ba2ce07db0447b251d7014f76c8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62324589"
---
# <a name="compiler-warning-level-4-c4690"></a>Advertencia del compilador (nivel 4) C4690

> \[ emitidl (pop)]: más elementos POP que Push

## <a name="remarks"></a>Comentarios

El atributo [emitidl](../../windows/emitidl.md) se extrajo una vez más de las que se ha insertado.

## <a name="example"></a>Ejemplo

El ejemplo siguiente genera la advertencia C4690: Para corregir este problema, asegúrese de que se extrae el atributo exactamente igual que muchas veces a medida que se inserta.

```cpp
// C4690.cpp
// compile with: /c /W4
[emitidl(pop)];   // C4690
class x {};
```
