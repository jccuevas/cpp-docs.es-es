---
title: _lsearch_s | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _lsearch_s
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
- api-ms-win-crt-utility-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _lsearch_s
- lsearch_s
dev_langs:
- C++
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
caps.latest.revision: 17
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
translationtype: Machine Translation
ms.sourcegitcommit: a937c9d083a7e4331af63323a19fb207142604a0
ms.openlocfilehash: 6f89899e5fe2c00cf17a7a18c9de2eac2ba8462f
ms.lasthandoff: 02/24/2017

---
# <a name="lsearchs"></a>_lsearch_s
Realiza una búsqueda lineal de un valor. Versión de [_lsearch](../../c-runtime-library/reference/lsearch.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
void *_lsearch_s(  
   const void *key,  
   void *base,  
   unsigned int *num,  
   size_t size,  
   int (__cdecl *compare)(void *, const void *, const void *),  
   void * context  
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `key`  
 Objeto que se va a buscar.  
  
 `base`  
 Puntero a la base de la matriz en la que se va a buscar.  
  
 `num`  
 Número de elementos.  
  
 `size`  
 Tamaño de cada elemento de la matriz expresado en bytes.  
  
 `compare`  
 Puntero a la rutina de comparación. El segundo parámetro es un puntero a la clave de búsqueda. El tercer parámetro es un puntero a un elemento de la matriz que se va a comparar con la clave.  
  
 `context`  
 Un puntero a un objeto al que se podría obtener acceso en la función de comparación.  
  
## <a name="return-value"></a>Valor devuelto  
 Si se encuentra `key`, `_lsearch_s` devuelve un puntero al elemento de la matriz en `base` que coincide con `key`. Si no se encuentra `key`, `_lsearch_s` devuelve un puntero al elemento recién agregado al final de la matriz.  
  
 Si se pasan parámetros no válidos a la función, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `NULL`. Para obtener más información, vea [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
### <a name="error-conditions"></a>Condiciones de error  
  
|`key`|`base`|`compare`|`num`|`size`|`errno`|  
|-----------|------------|---------------|-----------|------------|-------------|  
|`NULL`|cualquiera|cualquiera|cualquiera|cualquiera|`EINVAL`|  
|cualquiera|`NULL`|cualquiera|!= 0|cualquiera|`EINVAL`|  
|cualquiera|cualquiera|cualquiera|any|cero|`EINVAL`|  
|any|cualquiera|`NULL`|an|cualquiera|`EINVAL`|  
  
## <a name="remarks"></a>Comentarios  
 La función `_lsearch_s` realiza una búsqueda lineal del valor `key` en una matriz de `num` elementos, cada uno de ellos de `width` bytes. A diferencia de `bsearch_s`, para `_lsearch_s` no es necesario que la matriz esté ordenada. Si no se encuentra `key`, `_lsearch_s` lo agrega al final de la matriz e incrementa `num`.  
  
 La función `compare` es un puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y luego devuelve un valor que especifica su relación. La función `compare` también toma el puntero al contexto como primer argumento. `_lsearch_s` llama a `compare` una o varias veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada. `compare` debe comparar los elementos y luego devolver un valor distinto de cero (es decir, los elementos son diferentes) o 0 (es decir, los elementos son idénticos).  
  
 El puntero `context` puede ser útil si la estructura de datos de búsqueda forma parte de un objeto y la función `compare` necesita obtener acceso a los miembros del objeto. Por ejemplo, el código de la función `compare` puede convertir el puntero void en el tipo de objeto adecuado y acceder a los miembros de dicho objeto. La adición del puntero `context` hace que `_lsearch_s` sea más seguro, ya que puede usarse contexto adicional para evitar errores de reentrada asociados al uso de variables estáticas para que los datos estén disponibles para la función `compare`.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_lsearch_s`|\<search.h>|  
  
 Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md) en la introducción.  
  
## <a name="net-framework-equivalent"></a>Equivalente de .NET Framework  
 No es aplicable. Para llamar a la función estándar de C, use `PInvoke`. Para obtener más información, vea [Ejemplos de invocación de plataforma](http://msdn.microsoft.com/Library/15926806-f0b7-487e-93a6-4e9367ec689f).  
  
## <a name="see-also"></a>Vea también  
 [Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)   
 [bsearch_s](../../c-runtime-library/reference/bsearch-s.md)   
 [_lfind_s](../../c-runtime-library/reference/lfind-s.md)   
 [_lsearch](../../c-runtime-library/reference/lsearch.md)
