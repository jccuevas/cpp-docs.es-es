---
title: __uncaught_exception | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __uncaught_exception
apilocation:
- msvcrt.dll
- msvcr80.dll
- msvcr90.dll
- msvcr100.dll
- msvcr100_clr0400.dll
- msvcr110.dll
- msvcr110_clr0400.dll
- msvcr120.dll
- msvcr120_clr0400.dll
- ucrtbase.dll
apitype: DLLExport
f1_keywords: __uncaught_exception
dev_langs: C++
helpviewer_keywords: __uncaught_exception
ms.assetid: 4d9b75c6-c9c7-4876-b761-ea9ab1925e96
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 2b43a6b08087dcaeeda7959eaadbee9c250f4de9
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="uncaughtexception"></a>__uncaught_exception
Indica si se han producido una o más excepciones que aún no hayan sido controladas por el bloque `catch` correspondiente de una instrucción [try-catch](../../cpp/try-throw-and-catch-statements-cpp.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
bool __uncaught_exception(  
   );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 `true` desde el momento en que se produce una excepción en un bloque `try` hasta que el bloque `catch` coincidente se inicializa; de lo contrario, `false`.  
  
## <a name="remarks"></a>Comentarios  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|__uncaught_exception|eh.h|  
  
## <a name="see-also"></a>Vea también  
 [Instrucciones try, throw y catch (C++)](../../cpp/try-throw-and-catch-statements-cpp.md)