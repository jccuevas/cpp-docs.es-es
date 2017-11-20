---
title: __p__commode | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: __p__commode
apilocation:
- msvcr110.dll
- msvcrt.dll
- msvcr120.dll
- msvcr90.dll
- msvcr100.dll
- msvcr80.dll
- msvcr110_clr0400.dll
- api-ms-win-crt-stdio-l1-1-0.dll
apitype: DLLExport
f1_keywords: __p__commode
dev_langs: C++
helpviewer_keywords: __p__commode
ms.assetid: 4380acb8-e3e4-409c-a60f-6205ac5189ce
caps.latest.revision: "2"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: ef1a4830a994a5832b94f794e63046a0c081d55a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="pcommode"></a>__p__commode
Apunta a la variable global `_commode`, que especifica el *modo de confirmación de archivos* predeterminado para las operaciones de E/S de archivo.  
  
## <a name="syntax"></a>Sintaxis  
  
```cpp  
int * __p__commode(  
   );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Puntero a la variable global `_commode`.  
  
## <a name="remarks"></a>Comentarios  
 La función `__p__commode` es solo para uso interno y no debe llamarse desde código de usuario.  
  
 El modo de confirmación de archivos especifica cuándo se escriben datos críticos en el disco. Para obtener más información, consulte [fflush](../c-runtime-library/reference/fflush.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|__p\__commode|internal.h|