---
title: _free_locale | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _free_locale
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
- __free_locale
- free_locale
- _free_locale
dev_langs:
- C++
helpviewer_keywords:
- __free_locale function
- free_locale function
- locales, freeing
- _free_locale function
ms.assetid: 1f08d348-ab32-4028-a145-6cbd51b49af9
caps.latest.revision: 12
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
ms.openlocfilehash: c3582f51b4a66f33cf0926b12cbeccfc1f621c48
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="freelocale"></a>_free_locale
Libera un objeto de configuración regional.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void _free_locale(  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `locale`  
 Objeto de configuración regional que se va a liberar.  
  
## <a name="remarks"></a>Comentarios  
 La función `_free_locale` se usa para liberar el objeto de configuración regional obtenido de una llamada a `_get_current_locale` o `_create_locale`.  
  
 El nombre anterior de esta función, `__free_locale` (con dos caracteres de subrayado iniciales), ha quedado en desuso.  
  
## <a name="requirements"></a>Requisitos  
  
|`Routine`|Encabezado necesario|  
|---------------|---------------------|  
|`_free_locale`|\<locale.h>|  
  
 Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="see-also"></a>Vea también  
 [_get_current_locale](../../c-runtime-library/reference/get-current-locale.md)   
 [_create_locale, _wcreate_locale](../../c-runtime-library/reference/create-locale-wcreate-locale.md)
