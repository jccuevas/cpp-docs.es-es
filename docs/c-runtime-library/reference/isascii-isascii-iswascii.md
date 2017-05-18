---
title: isascii, __isascii, iswascii | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- iswascii
- __isascii
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
- api-ms-win-crt-string-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- iswascii
- istascii
- __isascii
- _istascii
- isascii
- ctype/isascii
- ctype/__isascii
- corecrt_wctype/iswascii
dev_langs:
- C++
helpviewer_keywords:
- __isascii function
- _isascii function
- isascii function
- _istascii function
- istascii function
- iswascii function
ms.assetid: ba4325ad-7cb3-4fb9-b096-58906d67971a
caps.latest.revision: 22
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.mt:
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
ms.sourcegitcommit: 3f91eafaf3b5d5c1b8f96b010206d699f666e224
ms.openlocfilehash: 401d8d05cc80ef1c72e7c72c06f94707b8c9848b
ms.contentlocale: es-es
ms.lasthandoff: 04/01/2017

---
# <a name="isascii-isascii-iswascii"></a>isascii, __isascii, iswascii
Determina si un carácter determinado es un carácter ASCII.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int __isascii(   
   int c   
);  
int iswascii(   
   wint_t c   
);  
#define isascii __isascii  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Entero que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter ASCII. `__isascii`Devuelve un valor distinto de cero si `c` es un carácter ASCII (en el intervalo 0 x 00 - 0x7F). `iswascii` devuelve un valor distinto de cero si `c` es una representación de caracteres anchos de un carácter ASCII. Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
## <a name="remarks"></a>Comentarios  
 Tanto `__isascii` como `iswascii` se implementan como macros, a menos que se defina la macro de preprocesador _CTYPE_DISABLE_MACROS.  
  
 Por motivos de compatibilidad con versiones anteriores, `isascii` se implementa como una macro solo si [__STDC\_\_](../../preprocessor/predefined-macros.md) no está definida o si está definida como 0; de lo contrario, está sin definir.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_istascii`|`__isascii`|`__isascii`|`iswascii`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`isascii`, `__isascii`|C: \<ctype.h><br /><br /> C++: \<cctype> o \<ctype.h>|  
|`iswascii`|C: \<wctype.h>, \<ctype.h> o \<wchar.h><br /><br /> C++: \<cwctype>, \<cctype>, \<wctype.h>, \<ctype.h> o \<wchar.h>|  
  
 Las funciones `isascii`, `__isascii` y `iswascii` son específicas de Microsoft. Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)
