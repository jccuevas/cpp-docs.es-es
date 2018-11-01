---
title: Error de las herramientas del vinculador LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: c5cbb9a7159a976ad0f96f46462669cff7b19f26
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50653731"
---
# <a name="linker-tools-error-lnk1201"></a>Error de las herramientas del vinculador LNK1201

Error al escribir en la base de datos de programa 'filename'; comprobar si hay suficiente espacio en disco, ruta de acceso no válido o no tiene suficientes privilegios

No se pudo escribir el vínculo a la base de datos de programa (PDB) para el archivo de salida.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Archivo está dañado. Elimine el archivo PDB y volver a vincular.

1. No hay suficiente espacio en disco para escribir el archivo.

1. Unidad no está disponible, posiblemente debido a un problema de red.

1. El depurador está activo en el programa que está intentando vincular.

1. Espacio en el montón.  Consulte [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) para obtener más información.