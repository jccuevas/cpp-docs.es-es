---
title: Convenciones de llamada obsoletas
ms.date: 11/04/2016
f1_keywords:
- __fortran
- __pascal
- __syscall
helpviewer_keywords:
- WINAPI [C++]
- __syscall keyword [C++]
- __pascal keyword [C++]
- __fortran keyword [C++]
- calling conventions, obsolete
ms.assetid: a91fc665-034a-48ce-b6bd-d27125f308a7
ms.openlocfilehash: 86c75c779158d9f191dd015410cf16c9ce25690d
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587998"
---
# <a name="obsolete-calling-conventions"></a>Convenciones de llamada obsoletas

## <a name="microsoft-specific"></a>Específicos de Microsoft

El **__pascal**, **__fortran**, y **__syscall** ya no se admiten las convenciones de llamada. Puede emular su funcionalidad mediante una de las convenciones de llamada admitidas y las opciones del vinculador adecuadas.

\<Windows.h > ahora es compatible con la macro WINAPI, que se traduce en la convención de llamada adecuada para el destino. Usar WINAPI donde antes utilizaba PASCAL o **__far \__pascal**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)