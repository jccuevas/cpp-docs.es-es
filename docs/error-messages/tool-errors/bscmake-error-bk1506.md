---
title: Error de BSCMAKE BK1506
ms.date: 11/04/2016
f1_keywords:
- BK1506
helpviewer_keywords:
- BK1506
ms.assetid: f51f8cea-f8fc-4323-bcf2-b7bd119792ee
ms.openlocfilehash: d1f74a90657985a87accc13bc2b576c1d7fd5a4e
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62279819"
---
# <a name="bscmake-error-bk1506"></a>Error de BSCMAKE BK1506

no se puede abrir el archivo 'filename' [: motivo]

BSCMAKE no puede abrir el archivo.

### <a name="to-fix-by-checking-the-following-possible-causes"></a>Posibles causas del error:

1. Archivo bloqueado por otro proceso. Si `reason` dice **ha denegado el permiso**, el explorador puede estar usando el archivo. Cierre la ventana del explorador y vuelva a intentar la compilación.

1. Disco lleno.

1. Error de hardware.

1. El archivo de salida especificado tiene el mismo nombre que un subdirectorio.