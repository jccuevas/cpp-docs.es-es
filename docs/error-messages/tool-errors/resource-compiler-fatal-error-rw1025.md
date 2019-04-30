---
title: Error irrecuperable del compilador de recursos RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 8ecfc11f5cc991294d966a4b6c75d8da6669d5b1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62347212"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Error irrecuperable del compilador de recursos RW1025

Memoria de montón far insuficiente

Compruebe si hay software residente en memoria que puede ocupar mucho espacio. Utilice el programa CHKDSK para averiguar cuánta memoria tiene.

Si va a crear un archivo de recursos grandes, divida el script de recursos en dos archivos. Después de crear dos archivos, use la línea de comandos de MS-DOS para combinarlas:

```
copy first.res /b + second.res /b full.res
```