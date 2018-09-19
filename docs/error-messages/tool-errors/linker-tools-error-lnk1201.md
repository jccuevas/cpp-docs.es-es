---
title: Las herramientas del vinculador LNK1201 Error | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1201
dev_langs:
- C++
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c133748f95846160e1387e31e023d9ce459b281
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46055280"
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