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
ms.openlocfilehash: 156482a395c7dfc8711e273141a09a37ea3e135d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80188563"
---
# <a name="obsolete-calling-conventions"></a>Convenciones de llamada obsoletas

**Específicos de Microsoft**

Ya no se admiten las convenciones de llamada de **__pascal**, **__fortran**y **__syscall** . Puede emular su funcionalidad mediante una de las convenciones de llamada admitidas y las opciones del vinculador adecuadas.

\<Windows. h > admite ahora la macro WINAPI, que se traduce en la Convención de llamada adecuada para el destino. Use WINAPI donde anteriormente usó PASCAL o **__far \__pascal**.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Consulte también

[Paso de argumentos y convenciones de nomenclatura](../cpp/argument-passing-and-naming-conventions.md)
