---
title: Las herramientas del vinculador LNK1106 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1106
dev_langs:
- C++
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 719ff1a87f3f1afc19cf38736c0059c46a8a9bdc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46110879"
---
# <a name="linker-tools-error-lnk1106"></a>Error de las herramientas del vinculador LNK1106

archivo no válido o disco lleno: no se puede buscar en ubicación

La herramienta no pudo leer o escribir en `location` en un archivo asignado a memoria.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Disco está lleno.

     Libere espacio y volver a vincular.

1. Intentando vincular a través de una red.

     Algunas redes no son totalmente compatibles con los archivos asignados a memoria utilizados por el vinculador. Intentar vincular en el disco local.

1. Bloque no válido en el disco.

     Aunque el sistema operativo y el hardware del disco deberían detectado un error de ese tipo, desea ejecutar un programa de comprobación de disco.

1. Espacio en el montón.

     Consulte [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) para obtener más información.