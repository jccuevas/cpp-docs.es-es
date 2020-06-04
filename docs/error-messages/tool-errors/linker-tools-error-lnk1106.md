---
title: Error de las herramientas del vinculador LNK1106
ms.date: 11/04/2016
f1_keywords:
- LNK1106
helpviewer_keywords:
- LNK1106
ms.assetid: 528f7e65-04be-4966-b8af-9276837c7cda
ms.openlocfilehash: 091d4e173bfb2eff8ffee2b5c30647f4d5e3bc04
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195375"
---
# <a name="linker-tools-error-lnk1106"></a>Error de las herramientas del vinculador LNK1106

archivo o disco no válido lleno: no se puede buscar en la ubicación

La herramienta no pudo leer ni escribir en `location` en un archivo asignado a la memoria.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Disco lleno.

   Libere espacio y vuelva a vincular.

1. Intentando vincular a través de una red.

   Algunas redes no admiten totalmente los archivos asignados a memoria que usa el enlazador. Intente vincular en el disco local.

1. Bloque incorrecto en el disco.

   Aunque el sistema operativo y el hardware del disco deberían haber detectado este tipo de error, es posible que desee ejecutar un programa de comprobación de disco.

1. Espacio de montón insuficiente.

   Vea [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) para obtener más información.
