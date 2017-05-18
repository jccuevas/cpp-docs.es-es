---
title: _getmbcp | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _getmbcp
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _getmbcp
- getmbcp
dev_langs:
- C++
helpviewer_keywords:
- code pages, determining current
- _getmbcp function
- getmbcp function
ms.assetid: 2db202d4-5c3d-4871-a0b8-ceb0b79ee7bb
caps.latest.revision: 13
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: df75a853a1982962b83d40c6e382e9c7d87a9c70
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="getmbcp"></a>_getmbcp
Recupera la página de códigos actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _getmbcp( void );  
```  
  
## <a name="return-value"></a>Valor devuelto  
 Devuelve la página de códigos multibyte actual. Un valor devuelto de 0 indica que se está usando una página de códigos de un solo byte.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_getmbcp`|\<mbctype.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="see-also"></a>Vea también  
 [_setmbcp](../../c-runtime-library/reference/setmbcp.md)
