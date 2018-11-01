---
title: Advertencia del compilador (niveles 2 y 3) C4008
ms.date: 11/04/2016
f1_keywords:
- C4008
helpviewer_keywords:
- C4008
ms.assetid: fb45e535-cb68-4743-80e9-a6e34cfffeca
ms.openlocfilehash: 99b78e1426cf1618e68ae74ae7e16dd0f08606ba
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50604092"
---
# <a name="compiler-warning-levels-2-and-3-c4008"></a>Advertencia del compilador (niveles 2 y 3) C4008

'identificador': atributo ' atributo ' omitido

El compilador omitió el atributo `__fastcall`, **estatic**o **inline** para una función (advertencia de nivel 3) o datos (advertencia de nivel 2).

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. El atributo`__fastcall` con datos.

1. Los atributos**static** o **inline** con la función **main** .