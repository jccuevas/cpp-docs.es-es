---
title: HUGE_VAL, _HUGE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
apiname:
- _HUGE
apilocation:
- msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
dev_langs:
- C++
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: c2d763b8c5379223ddacb8077c463efa0b91acfa
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32390510"
---
# <a name="hugeval-huge"></a>HUGE_VAL, _HUGE
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <math.h>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 `HUGE_VAL` es el mayor valor doble que se puede representar. Muchas funciones matemáticas en tiempo de ejecución devuelven este valor cuando se produce un error. Para algunas funciones, se devuelve -`HUGE_VAL`. `HUGE_VAL` se define como `_HUGE`, pero las funciones matemáticas en tiempo de ejecución devuelven `HUGE_VAL`. También debe usar `HUGE_VAL` en el código para mantener la coherencia.  
  
## <a name="see-also"></a>Vea también  
 [Constantes globales](../c-runtime-library/global-constants.md)