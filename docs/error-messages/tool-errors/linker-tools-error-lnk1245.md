---
title: Error de las herramientas del vinculador LNK1245
ms.date: 11/04/2016
f1_keywords:
- LNK1245
helpviewer_keywords:
- LNK1245
ms.assetid: 179c8165-ffbb-44cd-9f24-5250f29577cc
ms.openlocfilehash: 19e3f820b5bd7fdd8eac2f7b5a96fb5923ae0b92
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183805"
---
# <a name="linker-tools-error-lnk1245"></a>Error de las herramientas del vinculador LNK1245

subsistema no válido ' Subsystem ' especificado; /SUBSYSTEM debe ser WINDOWS, WINDOWSCE o CONSOLE

se usó [/CLR](../../build/reference/clr-common-language-runtime-compilation.md) para compilar el objeto y se cumple una de las condiciones siguientes:

- Se definió un punto de entrada personalizado ([/entry](../../build/reference/entry-entry-point-symbol.md)), de modo que el enlazador no pudo inferir un subsistema.

- Se pasó un valor a la opción del vinculador [/Subsystem](../../build/reference/subsystem-specify-subsystem.md) que no es válida para los objetos/CLR.

En ambos casos, la solución consiste en especificar un valor válido para la opción del vinculador/SUBSYSTEM.
