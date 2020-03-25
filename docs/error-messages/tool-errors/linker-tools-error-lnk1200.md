---
title: Error de las herramientas del vinculador LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: 9dcc37bd74a25e29726529346b1578bb8b18ac3e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80195141"
---
# <a name="linker-tools-error-lnk1200"></a>Error de las herramientas del vinculador LNK1200

Error al leer la base de datos del programa ' nombredearchivo '

No se pudo leer la base de datos de programa (PDB).

Este error puede deberse a daños en el archivo.

Si `filename` es el archivo PDB de un archivo objeto, vuelva a compilar el archivo objeto mediante [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Si `filename` es el archivo PDB del archivo de salida principal y este error se produjo durante un vínculo incremental, elimine el archivo PDB y revincule.
