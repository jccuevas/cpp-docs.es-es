---
title: Error del compilador C2588
ms.date: 11/04/2016
f1_keywords:
- C2588
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
ms.openlocfilehash: 15f9ba62751d9b3cb17ab56659310292dab41adf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62350457"
---
# <a name="compiler-error-c2588"></a>Error del compilador C2588

':: ~ identificador ': destructor global no válido

El destructor está definido para algo distinto de una clase, estructura o unión. Esto no está permitido.

Este error puede deberse a una falta de clase, estructura o nombre de unión en el lado izquierdo de la resolución de ámbito (`::`) operador.

El ejemplo siguiente genera C2588:

```
// C2588.cpp
~F();   // C2588
```