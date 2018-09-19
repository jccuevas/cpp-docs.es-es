---
title: _crtDbgFlag | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- _crtDbgFlag
- crtDbgFlag
dev_langs:
- C++
helpviewer_keywords:
- memory allocation, tracking flag
- crtDbgFlag constant
- _crtDbgFlag constant
- debug heap, tracking memory on
- debug heap, control flags
- enable memory allocation tracking flag
- memory, tracking on the debug heap
ms.assetid: 9e7adb47-8ab9-4e19-81d5-e2f237979973
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6d9900d42a5bae3c7a613028a7ae4ffe4bdc0333
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46044917"
---
# <a name="crtdbgflag"></a>_crtDbgFlag

La marca **_crtDbgFlag** consta de cinco campos de bits que controlan el modo en que las asignaciones de memoria en la versión de depuración del montón se siguen, comprueban, notifican y vuelcan. Los campos de bits de la marca se establecen mediante la función [_CrtSetDbgFlag](../c-runtime-library/reference/crtsetdbgflag.md). Esta marca y sus campos de bits se declaran en Crtdbg.h. Esta marca solo está disponible cuando se ha definido la marca [_DEBUG](../c-runtime-library/debug.md) en la aplicación.

Para obtener más información sobre el uso de esta marca junto con otras funciones de depuración, vea [Heap State Reporting Functions](/visualstudio/debugger/crt-debug-heap-details) (Funciones de notificación de estado de montón).

## <a name="see-also"></a>Vea también

[Marcas de control](../c-runtime-library/control-flags.md)