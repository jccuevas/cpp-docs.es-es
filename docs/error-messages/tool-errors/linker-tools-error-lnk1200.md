---
title: Error de las herramientas del vinculador LNK1200
ms.date: 11/04/2016
f1_keywords:
- LNK1200
helpviewer_keywords:
- LNK1200
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
ms.openlocfilehash: c99b25a83836f1ee0bc6ba622e42ea382c377172
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466838"
---
# <a name="linker-tools-error-lnk1200"></a>Error de las herramientas del vinculador LNK1200

Error al leer la base de datos de programa 'filename'

No se pudo leer la base de datos de programa (PDB).

Este error puede deberse a daños en el archivo.

Si `filename` es el archivo PDB de un archivo de objeto, vuelva a compilar el archivo de objeto mediante [/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).

Si `filename` es el archivo PDB para el archivo de salida principal, y este error se produjo durante una vinculación incremental, elimine el archivo PDB y volver a vincular.