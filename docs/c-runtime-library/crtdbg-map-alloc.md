---
title: _CRTDBG_MAP_ALLOC | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- CRTDBG_MAP_ALLOC
- _CRTDBG_MAP_ALLOC
dev_langs:
- C++
helpviewer_keywords:
- _CRTDBG_MAP_ALLOC macro
- memory allocation, in debug builds
- CRTDBG_MAP_ALLOC macro
ms.assetid: 435242b8-caea-4063-b765-4a608200312b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0c48095acceefa4bb4852dab18d35284492e7ba0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46069409"
---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC

Cuando la marca **_CRTDBG_MAP_ALLOC** se define en la versión de depuración de una aplicación, se asigna la versión base de las funciones del montón directamente a sus versiones de depuración. La marca se usa en Crtdbg.h para realizar la asignación. Esta marca solo está disponible cuando se ha definido la marca [_DEBUG](../c-runtime-library/debug.md) en la aplicación.

Para obtener más información sobre las ventajas de la versión de depuración y la versión base de una función del montón, consulte [Using the Debug Version Versus the Base Version](/visualstudio/debugger/debug-versions-of-heap-allocation-functions) (Uso de la versión de depuración en comparación con la versión base).

## <a name="see-also"></a>Vea también

[Marcas de control](../c-runtime-library/control-flags.md)