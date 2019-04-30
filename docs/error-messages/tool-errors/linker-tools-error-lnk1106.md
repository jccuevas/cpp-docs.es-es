---
title: Error de las herramientas del vinculador LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 7551e2f3f1efc90913981feb674f48aadb9ace51
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62255324"
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