---
title: Compilador advertencia (niveles 2 y 3) C4008 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4008
dev_langs:
- C++
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bd052b8dd6a0b70dd90ca076d0085675b33dc621
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46091184"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Advertencia del compilador (niveles 2 y 3) C4008

'identificador': atributo ' atributo ' omitido

El compilador omitió el atributo `__fastcall`, **estatic**o **inline** para una función (advertencia de nivel 3) o datos (advertencia de nivel 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. El atributo`__fastcall` con datos.

1. Los atributos**static** o **inline** con la función **main** .