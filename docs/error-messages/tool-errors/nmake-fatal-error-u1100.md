---
title: Error grave de NMAKE U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: d5c62c1465bbb6463afbac2bc9ad5f4290473471
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193269"
---
# <a name="nmake-fatal-error-u1100"></a>Error grave de NMAKE U1100

la macro ' nombremacro ' no es válida en el contexto de la regla de Batch ' rule '

NMAKE genera este error cuando el bloque de comandos de una regla de modo por lotes hace referencia directa o indirectamente a una macro de archivo especial que no es $ <.

$ < es la única macro permitida para las reglas de modo por lotes.
