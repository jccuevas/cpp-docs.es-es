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
ms.openlocfilehash: 7f059afe02cbbad77920fd8c4a0e6cb7c958e992
ms.sourcegitcommit: a6d63c07ab9ec251c48bc003ab2933cf01263f19
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/05/2019
ms.locfileid: "74857364"
---
# <a name="obsolete-calling-conventions"></a>Convenciones de llamada obsoletas

**Específicos de Microsoft**

Ya no se admiten las convenciones de llamada de **__pascal**, **__fortran**y **__syscall** . Puede emular su funcionalidad mediante una de las convenciones de llamada admitidas y las opciones del vinculador adecuadas.

\<Windows. h > admite ahora la macro WINAPI, que se traduce en la Convención de llamada adecuada para el destino. Use WINAPI donde anteriormente usó PASCAL o **__far \__pascal**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)