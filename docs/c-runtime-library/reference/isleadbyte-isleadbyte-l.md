---
title: isleadbyte, _isleadbyte_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _isleadbyte_l
- isleadbyte
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
- _istleadbyte
- _isleadbyte_l
- isleadbyte
dev_langs: C++
helpviewer_keywords:
- lead bytes
- _isleadbyte_l function
- _istleadbyte function
- istleadbyte function
- isleadbyte function
ms.assetid: 3b2bcf09-d82b-4803-9e80-59d04942802a
caps.latest.revision: "20"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: e6d679d634d14f3a762a6ef3d32d2ca4c5d4b6f0
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="isleadbyte-isleadbytel"></a>isleadbyte, _isleadbyte_l
Determina si un carácter es el byte inicial de un carácter multibyte.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea                  [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int isleadbyte(  
   int c   
);  
int _isleadbyte_l(  
   int c   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `c`  
 Entero que se va a probar.  
  
## <a name="return-value"></a>Valor devuelto  
 `isleadbyte` devuelve un valor distinto de cero si el argumento cumple la condición de prueba o 0 si no la cumple. En la configuración regional de "C" y en configuraciones regionales de juegos de caracteres de byte único (SBCS), `isleadbyte` devuelve siempre 0.  
  
## <a name="remarks"></a>Comentarios  
 La macro `isleadbyte` devuelve un valor distinto de cero si el argumento es el primer byte de un carácter multibyte. `isleadbyte`genera un resultado significativo para cualquier argumento entero comprendido entre -1 (`EOF`) a `UCHAR_MAX` (0xFF), ambos inclusive.  
  
 El tipo de argumento esperado de `isleadbyte` es `int`; si se pasa un carácter con signo, el compilador podría convertirlo en un entero por la extensión de signo y producir resultados imprevisibles.  
  
 La versión de esta función con el sufijo `_l` es idéntica, salvo que usa la configuración regional pasada en lugar de la configuración regional de su comportamiento dependiente de la configuración regional.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|------------------------------------|--------------------|-----------------------|  
|`_istleadbyte`|Siempre devuelve false|**_** `isleadbyte`|Siempre devuelve false|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`isleadbyte`|\<ctype.h>|  
|`_isleadbyte_l`|\<ctype.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Clasificación de bytes](../../c-runtime-library/byte-classification.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [_ismbb (Rutinas)](../../c-runtime-library/ismbb-routines.md)