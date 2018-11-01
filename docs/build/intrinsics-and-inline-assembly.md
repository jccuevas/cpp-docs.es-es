---
title: Ensamblado intrínseco y en línea
ms.date: 11/04/2016
ms.assetid: 8affd4bb-279d-46f3-851f-8be0a9c5ed3f
ms.openlocfilehash: 033225259c0a33414fe45eba313bb1f1c94eb379
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50515107"
---
# <a name="intrinsics-and-inline-assembly"></a>Ensamblado intrínseco y en línea

Una de las restricciones para el x64 compilador es no compatibles con el ensamblador alineado. Esto significa que las funciones que no se puede escribir en C o C++ tendrán que escribirse como subrutinas o funciones intrínsecas compatibles con el compilador. Algunas funciones son sensibles al rendimiento, mientras que otros no. Las funciones de sensibles al rendimiento deben implementarse como funciones intrínsecas.

En el que se describen las funciones intrínsecas compatibles con el compilador [intrínsecos del compilador](../intrinsics/compiler-intrinsics.md).

## <a name="see-also"></a>Vea también

[Convenciones de software x64](../build/x64-software-conventions.md)