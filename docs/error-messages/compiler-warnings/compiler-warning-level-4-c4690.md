---
title: Del compilador (nivel 4) de la advertencia C4690 | Microsoft Docs
ms.custom: ''
ms.date: 07/03/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4690
dev_langs:
- C++
helpviewer_keywords:
- C4690
ms.assetid: 080a0ea1-458b-477b-a37a-4a34c94709ff
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 04fb68bdab762f0f541849fad1568caff836b623
ms.sourcegitcommit: 26fff80635bd1d51bc51899203fddfea8b29b530
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/05/2018
ms.locfileid: "37853327"
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
