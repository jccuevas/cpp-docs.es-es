---
title: Error de las herramientas del vinculador LNK1201
ms.date: 11/04/2016
f1_keywords:
- LNK1201
helpviewer_keywords:
- LNK1201
ms.assetid: 64c3f496-a428-4b54-981e-faa82ef9c8a1
ms.openlocfilehash: 8d02743333c02c7cdff3b75e4a16bfecda442fa9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195115"
---
# <a name="linker-tools-error-lnk1201"></a>Error de las herramientas del vinculador LNK1201

Error al escribir en la base de datos de programa ' nombredearchivo '; Compruebe si hay espacio en disco insuficiente, ruta de acceso no válida o privilegios insuficientes

LINK no pudo escribir en la base de datos de programa (PDB) para el archivo de salida.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. El archivo está dañado. Elimine el archivo PDB y revincule.

1. No hay suficiente espacio en disco para escribir el archivo.

1. La unidad no está disponible, posiblemente debido a un problema de red.

1. El depurador está activo en el programa que está intentando vincular.

1. Espacio de montón insuficiente.  Vea [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) para obtener más información.
