---
title: _unlock | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _unlock
apilocation:
- msvcrt.dll
- msvcr100.dll
- msvcr110_clr0400.dll
- msvcr110.dll
- msvcr80.dll
- msvcr120.dll
- msvcr90.dll
- msvcr120_clr0400.dll
apitype: DLLExport
f1_keywords:
- unlock
- _unlock
dev_langs:
- C++
helpviewer_keywords:
- unlock function
- _unlock function
ms.assetid: 2eda2507-a134-4997-aa12-f2f8cb319e14
caps.latest.revision: 5
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
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 9d186187f486c0763a89e4edf3ff86e980d4d9df
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="unlock"></a>_unlock
Libera un bloqueo multiproceso.  
  
> [!IMPORTANT]
>  Esta función está obsoleta. A partir de Visual Studio 2015, no está disponible en CRT.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void __cdecl _unlock(  
   int locknum  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [in] `locknum`  
 El identificador del bloqueo que se liberará.  
  
## <a name="requirements"></a>Requisitos  
 **Origen:** mlock.c  
  
## <a name="see-also"></a>Vea también  
 [Referencia alfabética de funciones](../c-runtime-library/reference/crt-alphabetical-function-reference.md)   
 [_lock](../c-runtime-library/lock.md)
