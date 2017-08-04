---
title: _locking (Constantes) | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _LK_RLCK
- _LK_NBLCK
- _LK_LOCK
- _LK_NBRLCK
- _LK_UNLCK
dev_langs:
- C++
helpviewer_keywords:
- LK_UNLCK constant
- LK_NBRLCK constant
- _LK_NBRLCK constant
- _LK_NBLCK constant
- _LK_LOCK constant
- LK_NBLCK constant
- _LK_UNLCK constant
- LK_RLCK constant
- _LK_RLCK constant
- LK_LOCK constant
ms.assetid: c3dc92c8-60e3-4d29-9f50-5d217627c8ad
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 6e023de61dac5679d6c46c89b57255eef0b34c76
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="locking-constants"></a>_locking (Constantes)
## <a name="syntax"></a>Sintaxis  
  
```  
  
#include <sys/locking.h>  
  
```  
  
## <a name="remarks"></a>Comentarios  
 El argumento *mode* en la llamada a la función `_locking` especifica la acción de bloqueo que se va a realizar.  
  
 El argumento *mode* debe ser una de las siguientes constantes de manifiesto.  
  
 `_LK_LOCK`  
 Bloquea los bytes especificados. Si no se pueden bloquear los bytes, la función lo vuelve a intentar después de 1 segundo. Si, después de 10 intentos, no se pueden bloquear los bytes, la función devuelve un error.  
  
 `_LK_RLCK`  
 Igual a `_LK_LOCK`.  
  
 `_LK_NBLCK`  
 Bloquea los bytes especificados. Si no se pueden bloquear los bytes, la función devuelve un error.  
  
 `_LK_NBRLCK`  
 Igual a `_LK_NBLCK`.  
  
 `_LK_UNLCK`  
 Desbloquea los bytes especificados. (Los bytes deben haberse bloqueado previamente).  
  
## <a name="see-also"></a>Vea también  
 [_locking](../c-runtime-library/reference/locking.md)   
 [Constantes globales](../c-runtime-library/global-constants.md)
