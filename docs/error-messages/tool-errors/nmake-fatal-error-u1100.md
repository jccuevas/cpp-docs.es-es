---
title: Error grave de NMAKE U1100
ms.date: 11/04/2016
f1_keywords:
- U1100
helpviewer_keywords:
- U1100
ms.assetid: c71910a7-c581-4d9c-a38c-d2d557d56289
ms.openlocfilehash: a1474acab4ca4929fb4db4b7b78d7a96637a0745
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62298287"
---
# <a name="nmake-fatal-error-u1100"></a>Error grave de NMAKE U1100

la macro 'nombredemacro' no es válida en el contexto de la regla por lotes 'regla'

NMAKE genera este error cuando el bloque de comandos de una regla de modo por lotes directa o indirectamente hace referencia a una macro de archivo especial que no es de $<.

$< solo se permite la macro para las reglas de modo por lotes.