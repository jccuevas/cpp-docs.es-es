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
ms.openlocfilehash: ce6a8b2ef9ac807e48cff42186453666cebda5ee
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50055989"
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