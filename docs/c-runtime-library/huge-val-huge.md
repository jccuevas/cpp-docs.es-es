---
title: HUGE_VAL, _HUGE | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _HUGE
apilocation: msvcrt.dll
apitype: DLLExport
f1_keywords:
- _HUGE
- HUGE_VAL
dev_langs: C++
helpviewer_keywords:
- _HUGE constant
- HUGE_VAL constant
- double value
ms.assetid: 3f044b45-02cd-46b2-b1de-87fd0441dd6a
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 27fbb0ae4f8bbe658c37c0e979ea97a4dcec2fb3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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