---
title: Error del compilador C2588 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2588
dev_langs:
- C++
helpviewer_keywords:
- C2588
ms.assetid: 19a0cabd-ca13-44a5-9be3-ee676abf9bc4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d656dbde06d6052fd10611675f2cff8818cdb6e5
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108578"
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