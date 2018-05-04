---
title: _lsearch_s | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 12315350b62673abb0a838f9d30830354c58da73
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="lsearchs"></a>_lsearch_s

Realiza una búsqueda lineal de un valor. Versión de [_lsearch](lsearch.md) con mejoras de seguridad, como se explica en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

## <a name="syntax"></a>Sintaxis

```C
void *_lsearch_s(
   const void *key,
   void *base,
   unsigned int *num,
   size_t size,
   int (__cdecl *compare)(void *, const void *, const void *),
   void * context
);
```

### <a name="parameters"></a>Parámetros

*key*<br/>
Objeto que se va a buscar.

*base*<br/>
Puntero a la base de la matriz en la que se va a buscar.

*Número*<br/>
Número de elementos.

*size*<br/>
Tamaño de cada elemento de la matriz expresado en bytes.

*compare*<br/>
Puntero a la rutina de comparación. El segundo parámetro es un puntero a la clave de búsqueda. El tercer parámetro es un puntero a un elemento de la matriz que se va a comparar con la clave.

*Contexto*<br/>
Un puntero a un objeto al que se podría obtener acceso en la función de comparación.

## <a name="return-value"></a>Valor devuelto

Si *clave* se encuentra, **_lsearch_s** devuelve un puntero al elemento de la matriz en *base* que coincida con *clave*. Si *clave* no se encuentra, **_lsearch_s** devuelve un puntero al elemento recién agregado al final de la matriz.

Si se pasan parámetros no válidos a la función, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, a continuación, **errno** está establecido en **EINVAL** y la función devuelve **NULL**. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Condiciones de error

|*key*|*base*|*compare*|*Número*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|cero|**EINVAL**|
|any|any|**NULL**|an|any|**EINVAL**|

## <a name="remarks"></a>Comentarios

El **_lsearch_s** función realiza una búsqueda lineal para el valor *clave* en una matriz de *número* elementos, cada uno de los *ancho* bytes. A diferencia de **bsearch_s**, **_lsearch_s** no requiere que la matriz se ordenen. Si *clave* no se encuentra, a continuación, **_lsearch_s** lo agrega al final de la matriz y se incrementa *número*.

El *comparar* función es un puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y devuelve un valor que especifica la relación. El *comparar* función también toma el puntero en el contexto como el primer argumento. **_lsearch_s** llamadas *comparar* una o varias veces durante la búsqueda, pasar punteros a dos elementos de la matriz en cada llamada. *comparar* debe comparar los elementos y, a continuación, devolver uno distinto de cero (es decir, los elementos son diferentes) o 0 (es decir, los elementos son idénticos).

El *contexto* puntero puede ser útil si la estructura de datos de búsqueda es parte de un objeto y el *comparar* función necesita tener acceso a los miembros del objeto. Por ejemplo, el código de la *comparar* función puede convertir el puntero void en los miembros de tipo y el acceso de objeto correspondiente de ese objeto. La adición de la *contexto* puntero hace **_lsearch_s** más segura, porque puede usarse contexto adicional para evitar errores de reentrada asociados con el uso de variables estáticas para disponer de datos para el *comparar* función.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Buscar y ordenar](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
