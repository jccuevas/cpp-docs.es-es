---
title: wctype | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: wctype
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
f1_keywords: wctype
dev_langs: C++
helpviewer_keywords:
- wctype function
- wide characters
ms.assetid: 14aded12-4087-4123-bc48-db4e10999223
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: daae662a39d012418b5cd178e26d731dbca1e715
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="wctype"></a>wctype
Determina una regla de clasificación para códigos de caracteres anchos.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
wctype_t wctype(  
   const char * property   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `property`  
 Cadena de propiedad.  
  
## <a name="return-value"></a>Valor devuelto  
 Si la categoría `LC_CTYPE` de la configuración regional actual no define una regla de clasificación cuyo nombre coincida con la cadena de propiedad `property`, la función devuelve cero. De lo contrario, devuelve un valor distinto de cero adecuado como segundo argumento de una llamada subsiguiente a [towctrans](../../c-runtime-library/reference/towctrans.md).  
  
## <a name="remarks"></a>Comentarios  
 La función determina una regla de clasificación para códigos de caracteres anchos. Los siguientes pares de llamadas tienen el mismo comportamiento en todas las configuraciones regionales (aunque una implementación puede definir reglas de clasificación adicionales incluso en la configuración regional "C"):  
  
|Función|Igual que|  
|--------------|-------------|  
|`iswalnum(`  `c`  `)`|`iswctype(`  `c` `, wctype( "alnum" ) )`|  
|`iswalpha(`  `c`  `)`|`iswctype(`  `c` `, wctype( "alpha" ) )`|  
|`iswcntrl(`  `c`  `)`|`iswctype(`  `c` `, wctype( "cntrl" ) )`|  
|`iswdigit(`  `c`  `)`|`iswctype(`  `c` `, wctype( "digit" ) )`|  
|`iswgraph(`  `c`  `)`|`iswctype(`  `c` `, wctype( "graph" ) )`|  
|`iswlower(`  `c`  `)`|`iswctype(`  `c` `, wctype( "lower" ) )`|  
|`iswprint(`  `c`  `)`|`iswctype(`  `c` `, wctype( "print" ) )`|  
|`iswpunct(`  `c`  `)`|`iswctype(`  `c` `, wctype( "punct" ) )`|  
|`iswspace(`  `c`  `)`|`iswctype(`  `c` `, wctype( "space" ) )`|  
|`iswupper(`  `c`  `)`|`iswctype(`  `c` `, wctype( "upper" ) )`|  
|`iswxdigit(`  `c`  `)`|`iswctype(`  `c` `, wctype( "xdigit" ) )`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`wctype`|\<wctype.h>|  
  
 Para obtener información adicional de compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la Introducción.  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [setlocale, _wsetlocale](../../c-runtime-library/reference/setlocale-wsetlocale.md)