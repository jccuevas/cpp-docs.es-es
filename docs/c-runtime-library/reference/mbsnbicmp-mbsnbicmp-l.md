---
title: _mbsnbicmp, _mbsnbicmp_l | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _mbsnbicmp_l
- _mbsnbicmp
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
- api-ms-win-crt-multibyte-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _strnicmp
- _wcsnicmp_l
- _mbsnbicmp
- mbsnbicmp
- mbsnbicmp_l
- _tcsnicmp
- _strnicmp_l
- _tcsnicmp_l
- _wcsnicmp
- _mbsnbicmp_l
dev_langs:
- C++
helpviewer_keywords:
- _tcsnicmp_l function
- _strnicmp function
- mbsnbicmp_l function
- _wcsnicmp_l function
- _mbsnbicmp function
- _mbsnbicmp_l function
- _tcsnicmp function
- _strnicmp_l function
- mbsnbicmp function
- _wcsnicmp function
ms.assetid: ddb44974-8b0c-42f0-90d0-56c9350bae0c
caps.latest.revision: 16
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
ms.openlocfilehash: 3eff360605f782a2a159195a91dfc3d97da2cb8a
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="mbsnbicmp-mbsnbicmpl"></a>_mbsnbicmp, _mbsnbicmp_l
Compara `n` bytes de dos cadenas de caracteres multibyte, sin distinción de mayúsculas y minúsculas.  
  
> [!IMPORTANT]
>  Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para más información, vea [Funciones de CRT no admitidas con /ZW](http://msdn.microsoft.com/library/windows/apps/jj606124.aspx).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _mbsnbicmp(  
   const unsigned char *string1,  
   const unsigned char *string2,  
   size_t count   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `string1, string2`  
 Cadenas terminadas en NULL que se van a comparar.  
  
 `count`  
 Número de bytes que se van a comparar.  
  
## <a name="return-value"></a>Valor devuelto  
 El valor devuelto indica la relación entre las subcadenas.  
  
|Valor devuelto|Descripción|  
|------------------|-----------------|  
|< 0|La subcadena `string1` es menor que la subcadena `string2`.|  
|0|La subcadena `string1` es idéntica a la subcadena `string2`.|  
|> 0|La subcadena `string1` es mayor que la subcadena `string2`.|  
  
 Si se produce un error, `_mbsnbcmp` devuelve `_NLSCMPERROR`, que se define en String.h y Mbstring.h.  
  
## <a name="remarks"></a>Comentarios  
 La función `_mbsnbicmp` realiza una comparación ordinal de, a lo sumo, los primeros `count` bytes de `string1` y `string2`. La comparación se realiza mediante la conversión de cada carácter a minúscula. `_mbsnbcmp` es una versión de `_mbsnbicmp` que distingue entre mayúsculas y minúsculas. La comparación finaliza si se llega a un carácter nulo de terminación en una de las cadenas antes de que se comparen `count` caracteres. Si las cadenas son iguales cuando se llega a un carácter nulo de terminación en una de las cadenas antes de que se comparen `count` caracteres, la cadena más corta es menor.  
  
 `_mbsnbicmp` es similar a `_mbsnicmp`, salvo por que compara cadenas hasta los `count` bytes, en lugar de caracteres.  
  
 Dos cadenas que contienen caracteres situados entre la 'Z' y la 'a' en la tabla ASCII ('[', '\\', ']', '^', '_' y '\`') se comparan de forma distinta. Por ejemplo, las dos cadenas "`ABCDE`" y "`ABCD^`" se comparan de una manera si la comparación es en minúscula ("`abcde`" > "`abcd^`") y de otra si es en mayúscula ("`ABCDE`" < "`ABCD^`").  
  
 `_mbsnbicmp` reconoce las secuencias de caracteres multibyte de acuerdo con la [página de códigos multibyte](../../c-runtime-library/code-pages.md) que se está usando. La configuración regional actual no le afecta.  
  
 Si `string1` o `string2` es un puntero nulo, `_mbsnbicmp` invoca el controlador de parámetros no válidos, tal como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función devuelve `_NLSCMPERROR` y establece en `errno` en `EINVAL`.  
  
### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico  
  
|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|  
|---------------------|--------------------------------------|--------------------|-----------------------|  
|`_tcsnicmp`|`_strnicmp`|`_mbsnbicmp`|`_wcsnicmp`|  
|`_tcsnicmp_l`|`_strnicmp_l`|`_mbsnbicmp_l`|`_wcsnicmp_l`|  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_mbsnbicmp`|<mbstring.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="example"></a>Ejemplo  
 Vea el ejemplo de [_mbsnbcmp, _mbsnbcmp_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md).  
  
## <a name="see-also"></a>Vea también  
 [Manipulación de cadenas](../../c-runtime-library/string-manipulation-crt.md)   
 [_mbsnbcat, _mbsnbcat_l](../../c-runtime-library/reference/mbsnbcat-mbsnbcat-l.md)   
 [_mbsnbcmp, _mbsnbcmp_l](../../c-runtime-library/reference/mbsnbcmp-mbsnbcmp-l.md)   
 [_stricmp, _wcsicmp, _mbsicmp, _stricmp_l, _wcsicmp_l, _mbsicmp_l](../../c-runtime-library/reference/stricmp-wcsicmp-mbsicmp-stricmp-l-wcsicmp-l-mbsicmp-l.md)
