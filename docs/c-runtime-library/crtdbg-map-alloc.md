---
title: _CRTDBG_MAP_ALLOC | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 8
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
translationtype: Human Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 709ba57e3cca392d2440c7ad528125dc31070cac
ms.lasthandoff: 02/24/2017

---
# <a name="crtdbgmapalloc"></a>_CRTDBG_MAP_ALLOC
Cuando la marca **_CRTDBG_MAP_ALLOC** se define en la versión de depuración de una aplicación, se asigna la versión base de las funciones del montón directamente a sus versiones de depuración. La marca se usa en Crtdbg.h para realizar la asignación. Esta marca solo está disponible cuando se ha definido la marca [_DEBUG](../c-runtime-library/debug.md) en la aplicación.  
  
 Para obtener más información sobre las ventajas de la versión de depuración y la versión base de una función del montón, consulte [Using the Debug Version Versus the Base Version](/visualstudio/debugger/debug-versions-of-heap-allocation-functions) (Uso de la versión de depuración en comparación con la versión base).  
  
## <a name="see-also"></a>Vea también  
 [Marcas de control](../c-runtime-library/control-flags.md)
