---
title: Error irrecuperable del compilador de recursos RW1025
ms.date: 11/04/2016
f1_keywords:
- RW1025
helpviewer_keywords:
- RW1025
ms.assetid: 561a02af-e7e0-442a-8ad3-a00b2ca1b62e
ms.openlocfilehash: 9b6697dff0a445cc342f30d08bd79822b02df7b8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80172731"
---
# <a name="resource-compiler-fatal-error-rw1025"></a>Error irrecuperable del compilador de recursos RW1025

Memoria de montón lejana

Compruebe si hay software residente en memoria que puede ocupar demasiado espacio. Use el programa CHKDSK para averiguar cuánta memoria tiene.

Si va a crear un archivo de recursos de gran tamaño, divida el script de recursos en dos archivos. Después de crear dos archivos. res, use la línea de comandos de MS-DOS para unirlos juntos:

```
copy first.res /b + second.res /b full.res
```
