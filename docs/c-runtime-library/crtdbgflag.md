---
title: _crtDbgFlag
ms.date: 11/04/2016
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
ms.openlocfilehash: 5abb0418b5ffb1f95bf7b362f621f99f411094d6
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50435300"
---
# <a name="crtdbgflag"></a>_crtDbgFlag

La marca **_crtDbgFlag** consta de cinco campos de bits que controlan el modo en que las asignaciones de memoria en la versión de depuración del montón se siguen, comprueban, notifican y vuelcan. Los campos de bits de la marca se establecen mediante la función [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md). Esta marca y sus campos de bits se declaran en Crtdbg.h. Esta marca solo está disponible cuando se ha definido la marca [_DEBUG](../c-runtime-library/debug.md) en la aplicación.

Para obtener más información sobre el uso de esta marca junto con otras funciones de depuración, vea [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details) (Funciones de notificación de estado de montón).

## <a name="see-also"></a>Vea también

[Marcas de control](../c-runtime-library/control-flags.md)