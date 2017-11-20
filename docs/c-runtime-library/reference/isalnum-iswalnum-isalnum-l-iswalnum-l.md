---
title: isalnum, iswalnum, _isalnum_l, _iswalnum_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _iswalnum_l
- _isalnum_l
- iswalnum
- isalnum
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
- _istalnum_l
- _iswalnum_l
- iswalnum
- _isalnum_l
- isalnum
- _istalnum
dev_langs: C++
helpviewer_keywords:
- _istalnum function
- _ismbcalnum_l function
- iswalnum function
- isalnum function
- istalnum function
- _isalnum_l function
- _istalnum_l function
- _iswalnum_l function
ms.assetid: 0dc51306-ade8-4944-af27-e4176fc89093
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 25207b525ec1c5e4c19d114281a0daff2d38ea1f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="isalnum-iswalnum-isalnuml-iswalnuml"></a>isalnum, iswalnum, _isalnum_l, _iswalnum_l
Determina si un entero representa un carácter alfanumérico.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int isalnum(   
   int c   
);  
int iswalnum(   
   wint_t c   
);  
int _isalnum_l(   
   int c,  
   _locale_t locale  
);  
int _iswalnum_l(   
   wint_t c,  
   _locale_t locale  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Entero que se va a probar.  
  
 `locale`  
 Configuración regional que se va a usar.  
  
## <a name="return-value"></a>Valor devuelto  
 Cada una de estas rutinas devuelve un valor distinto de cero si `c` es una representación concreta de un carácter alfanumérico. `isalnum`Devuelve un valor distinto de cero si el valor `isalpha` o `isdigit` es distinto de cero para `c`, es decir, si `c` está en los intervalos A - Z, a - z, o 0 - 9. `iswalnum` devuelve un valor distinto de cero si `iswalpha` o `iswdigit` es distinto de cero para `c`. Cada una de estas rutinas devuelve 0 si `c` no cumple la condición de prueba.  
  
 Las versiones de estas funciones que tienen el sufijo `_l` usan el parámetro de configuración regional que se pasa en lugar de la configuración regional actual. Para obtener más información, vea [Configuración regional](../../c-runtime-library/locale.md).  
  
 El comportamiento de `isalnum` e `_isalnum_l` es indefinido si `c` no se encuentra al final del archivo ni en el intervalo de 0 a 0xFF, incluidos. Cuando se usa una biblioteca CRT de depuración y `c` no es uno de estos valores, las funciones generan una aserción.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istalnum`|`isalnum`|[_ismbcalnum](../../c-runtime-library/reference/ismbcalnum-functions.md)|`iswalnum`|  
|`_istalnum_l`|`_isalnum_l`|`_ismbcalnum_l`|`_iswalnum_l`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`isalnum`|\<ctype.h>|  
|`iswalnum`|\<ctype.h> o \<wchar.h>|  
|`_isalnum_l`|\<ctype.h>|  
|`_iswalnum_l`|\<ctype.h> o \<wchar.h>|  
  
 Para obtener información adicional sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de caracteres](../../c-runtime-library/character-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [is, isw (Rutinas)](../../c-runtime-library/is-isw-routines.md)