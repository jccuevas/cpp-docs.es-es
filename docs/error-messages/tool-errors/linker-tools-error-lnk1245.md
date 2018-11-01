---
title: Error de las herramientas del vinculador LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 4cf9a6c4356872b727a10a360396e51e38928b29
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505487"
---
# <a name="linker-tools-error-lnk1245"></a>Error de las herramientas del vinculador LNK1245

subsistema 'subsistema' especificado; /SUBSYSTEM debe ser WINDOWS, WINDOWSCE o CONSOLE

[/ CLR](../../build/reference/clr-common-language-runtime-compilation.md) se utilizó para compilar el objeto y una de las siguientes condiciones era true:

- Se ha definido un punto de entrada personalizado ([/Entry](../../build/reference/entry-entry-point-symbol.md)), de modo que el vinculador no puede inferir un subsistema.

- Se pasó un valor a la [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) opción del vinculador que no es válido para los objetos / CLR.

En ambos casos, la resolución es especificar un valor válido para la opción de vinculador/SUBSYSTEM.