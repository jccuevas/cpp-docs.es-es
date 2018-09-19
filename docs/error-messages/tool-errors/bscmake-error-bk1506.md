---
title: Error de BSCMAKE BK1506 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- BK1506
dev_langs:
- C++
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 26201a894212701cca19ab2192676b37a69e8b57
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46088701"
---
# <a name="bscmake-error-bk1506"></a>Error de BSCMAKE BK1506

no se puede abrir el archivo 'filename' [: motivo]

BSCMAKE no puede abrir el archivo.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Archivo bloqueado por otro proceso. Si `reason` dice **ha denegado el permiso**, el explorador puede estar usando el archivo. Cierre la ventana del explorador y vuelva a intentar la compilación.

1. Disco lleno.

1. Error de hardware.

1. El archivo de salida especificado tiene el mismo nombre que un subdirectorio.