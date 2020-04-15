---
title: _lsearch_s
ms.date: 4/2/2020
api_name:
- _lsearch_s
- _o__lsearch_s
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
- api-ms-win-crt-private-l1-1-0
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
ms.openlocfilehash: 720b83dd48b42d77f35bce12f16e8ac79eb3b4d3
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81341649"
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

*Tamaño*<br/>
Tamaño de cada elemento de la matriz expresado en bytes.

*Comparar*<br/>
Puntero a la rutina de comparación. El segundo parámetro es un puntero a la clave de búsqueda. El tercer parámetro es un puntero a un elemento de la matriz que se va a comparar con la clave.

*contextoo*<br/>
Un puntero a un objeto al que se podría obtener acceso en la función de comparación.

## <a name="return-value"></a>Valor devuelto

Si se encuentra la *clave,* **_lsearch_s** devuelve un puntero al elemento de la matriz en *la base* que coincide con la *clave*. Si no se encuentra la *clave,* **_lsearch_s** devuelve un puntero al elemento recién agregado al final de la matriz.

Si se pasan parámetros no válidos a la función, se invoca el controlador de parámetros no válidos, como se describe en validación de [parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **NULL**. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

### <a name="error-conditions"></a>Condiciones de error

|*key*|*base*|*Comparar*|*number*|*Tamaño*|**errno**|
|-----------|------------|---------------|-----------|------------|-------------|
|**Null**|cualquiera|cualquiera|cualquiera|cualquiera|**EINVAL**|
|cualquiera|**Null**|cualquiera|!= 0|cualquiera|**EINVAL**|
|cualquiera|cualquiera|cualquiera|cualquiera|cero|**EINVAL**|
|cualquiera|cualquiera|**Null**|an|cualquiera|**EINVAL**|

## <a name="remarks"></a>Observaciones

La función **_lsearch_s** realiza una búsqueda lineal de la *clave* de valor en una matriz de elementos *numéricos,* cada uno de bytes de *ancho.* A diferencia **de bsearch_s**, **_lsearch_s** no requiere que se ordene la matriz. Si no se encuentra la *clave,* **_lsearch_s** la agrega al final de la matriz e incrementa el *número*.

La función *compare* es un puntero a una rutina proporcionada por el usuario que compara dos elementos de matriz y devuelve un valor que especifica su relación. La función *compare* también toma el puntero al contexto como primer argumento. **_lsearch_s** llamadas *se comparan* una o más veces durante la búsqueda, pasando punteros a dos elementos de matriz en cada llamada. *comparar* debe comparar los elementos y, a continuación, devolver distinto de cero (lo que significa que los elementos son diferentes) o 0 (lo que significa que los elementos son idénticos).

El puntero de *contexto* puede ser útil si la estructura de datos buscada forma parte de un objeto y la función *de comparación* necesita tener acceso a los miembros del objeto. Por ejemplo, el código de la función *compare* puede convertir el puntero void en el tipo de objeto adecuado y tener acceso a los miembros de ese objeto. La adición del puntero de *contexto* **hace que _lsearch_s** sea más seguro porque se puede usar contexto adicional para evitar errores de reentrada asociados con el uso de variables estáticas para que los datos estén disponibles para la función de *comparación.*

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_lsearch_s**|\<search.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Búsqueda y clasificación](../../c-runtime-library/searching-and-sorting.md)<br/>
[bsearch_s](bsearch-s.md)<br/>
[_lfind_s](lfind-s.md)<br/>
[_lsearch](lsearch.md)<br/>
