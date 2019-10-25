---
title: _lsearch_s
ms.date: 11/04/2016
api_name:
- _lsearch_s
api_location:
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _lsearch_s
- lsearch_s
helpviewer_keywords:
- linear searching
- values, searching for
- keys, finding in arrays
- arrays [CRT], searching
- searching, linear
- _lsearch_s function
- lsearch_s function
ms.assetid: d2db0635-be7a-4799-8660-255f14450882
ms.openlocfilehash: 1c3c0ac41a4805acb558c75fb5ff4cbc0e3aa838
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70953018"
---
# <a name="_lsearch_s"></a>_lsearch_s

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

*number*<br/>
Número de elementos.

*size*<br/>
Tamaño de cada elemento de la matriz expresado en bytes.

*compare*<br/>
Puntero a la rutina de comparación. El segundo parámetro es un puntero a la clave de búsqueda. El tercer parámetro es un puntero a un elemento de la matriz que se va a comparar con la clave.

*context*<br/>
Un puntero a un objeto al que se podría obtener acceso en la función de comparación.

## <a name="return-value"></a>Valor devuelto

Si se encuentra la *clave* , **_lsearch_s** devuelve un puntero al elemento de la matriz en la *base* que coincide con la *clave*. Si no se encuentra la *clave* , **_lsearch_s** devuelve un puntero al elemento recién agregado al final de la matriz.

Si se pasan parámetros no válidos a la función, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **null**. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Condiciones de error

|*key*|*base*|*compare*|*number*|*size*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**NULL**|any|any|any|any|**EINVAL**|
|any|**NULL**|any|!= 0|any|**EINVAL**|
|any|any|any|any|cero|**EINVAL**|
|any|any|**NULL**|an|any|**EINVAL**|

## <a name="remarks"></a>Comentarios

La función **_lsearch_s** realiza una búsqueda lineal de la *clave* Value en una matriz de elementos *Number* , cada uno de los bytes de *ancho* . A diferencia de **bsearch_s**, **_lsearch_s** no requiere la ordenación de la matriz. Si no se encuentra la *clave* , **_lsearch_s** la agrega al final de la matriz e incrementa el *número*.

La función de *comparación* es un puntero a una rutina proporcionada por el usuario que compara dos elementos de la matriz y devuelve un valor que especifica su relación. La función *Compare* también toma el puntero al contexto como primer argumento. las llamadas a **_lsearch_s** *comparan* una o más veces durante la búsqueda, pasando punteros a dos elementos de la matriz en cada llamada. *Compare* debe comparar los elementos y, a continuación, devolver un valor distinto de cero (lo que significa que los elementos son diferentes) o 0 (lo que significa que los elementos son idénticos).

El puntero de *contexto* puede ser útil si la estructura de datos de búsqueda forma parte de un objeto y la función de *comparación* necesita acceder a los miembros del objeto. Por ejemplo, el código de la función *Compare* puede convertir el puntero void en el tipo de objeto adecuado y acceder a los miembros de ese objeto. La adición del puntero de *contexto* hace que **_lsearch_s** sea más seguro, ya que puede usarse contexto adicional para evitar errores de reentrada asociados al uso de variables estáticas para que los datos estén disponibles para la función de *comparación* .

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
