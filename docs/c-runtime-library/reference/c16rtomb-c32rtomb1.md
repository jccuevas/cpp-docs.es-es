---
title: c16rtomb, c32rtomb1 | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- c16rtomb
- c32rtomb
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
- api-ms-win-crt-convert-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- c16rtomb
- c32rtomb
- uchar/c16rtomb
- uchar/c32rtomb
dev_langs: C++
helpviewer_keywords:
- c16rtomb function
- c32rtomb function
ms.assetid: 7f5743ca-a90e-4e3f-a310-c73e16f4e14d
caps.latest.revision: "3"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9eb43d6b225bce002eb2ce5293cb048d3062bcd5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="c16rtomb-c32rtomb"></a>c16rtomb, c32rtomb
Convierte un carácter ancho UTF-16 o UTF-32 en un carácter multibyte en la configuración regional actual.  
  
## <a name="syntax"></a>Sintaxis  
  
```  
size_t c16rtomb(  
    char *mbchar,   
    char16_t wchar,  
    mbstate_t *state  
);  
size_t c32rtomb(  
    char *mbchar,   
    char32_t wchar,  
    mbstate_t *state  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 [out] `mbchar`  
 Puntero a una matriz para almacenar el carácter convertido multibyte.  
  
 [in] `wchar`  
 Carácter ancho que se va a convertir.  
  
 [in, out] `state`  
 Puntero a un objeto `mbstate_t` .  
  
## <a name="return-value"></a>Valor devuelto  
 El número de bytes almacenados en el objeto de matriz `mbchar`, incluidas las secuencias de desplazamiento. Si `wchar` no es un carácter ancho válido, se devuelve el valor (`size_t`)(-1), `errno` se establece en `EILSEQ`y no se especifica el valor de `state` .  
  
## <a name="remarks"></a>Comentarios  
 La función `c16rtomb` convierte el carácter UTF-16 `wchar` a la secuencia de caracteres estrechos multibyte equivalentes en la configuración regional actual. Si `mbchar` no es un puntero nulo, la función almacena la secuencia convertida en el objeto de matriz al que señala `mbchar`. Se almacenan hasta `MB_CUR_MAX` bytes en `mbchar`, y `state` se establece en el estado de desplazamiento multibyte resultante.    Si `wchar` es un carácter ancho nulo, se almacena una secuencia necesaria para restaurar el estado de desplazamiento inicial, si es necesario, seguido del carácter nulo y `state` se establece en el estado de conversión inicial. La función `c32rtomb` es idéntica, pero convierte un carácter UTF-32.  
  
 Si `mbchar` es un puntero nulo, el comportamiento equivale a una llamada a la función que sustituye un búfer interno para `mbchar` y un carácter nulo ancho para `wchar`.  
  
 El objeto de estado de conversión `state` le permite realizar llamadas posteriores a esta función y otras funciones reiniciables que mantienen el estado de desplazamiento de los caracteres multibyte de salida. Resultados son indefinidos al mezclar el uso de funciones reiniciables y no reiniciables, o si se realiza una llamada a `setlocale` entre las llamadas a funciones reiniciables.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`c16rtomb`, `c32rtomb`|C, C++: \<uchar.h>|  
  
 Para obtener información sobre la compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="see-also"></a>Vea también  
 [Conversión de datos](../../c-runtime-library/data-conversion.md)   
 [Configuración regional](../../c-runtime-library/locale.md)   
 [Interpretación de secuencias de caracteres multibyte](../../c-runtime-library/interpretation-of-multibyte-character-sequences.md)   
 [mbrtoc16, mbrtoc32](../../c-runtime-library/reference/mbrtoc16-mbrtoc323.md)   
 [wcrtomb](../../c-runtime-library/reference/wcrtomb.md)   
 [wcrtomb_s](../../c-runtime-library/reference/wcrtomb-s.md)