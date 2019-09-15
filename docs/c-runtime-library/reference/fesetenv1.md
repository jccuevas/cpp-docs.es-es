---
title: fesetenv
ms.date: 04/05/2018
api_name:
- fesetenv
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
- api-ms-win-crt-runtime-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- fesetenv
- fenv/fesetenv
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
ms.openlocfilehash: 155b9f635f6e8c3dc5acb61126f41c49cd32601f
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941108"
---
# <a name="fesetenv"></a>fesetenv

Establece el entorno actual de punto flotante.

## <a name="syntax"></a>Sintaxis

```C
int fesetenv(
   const fenv_t *penv
);
```

### <a name="parameters"></a>Parámetros

*penv*<br/>
Puntero a un objeto **fenv_t** que contiene un entorno de punto flotante establecido por una llamada a [fegetenv](fegetenv1.md) o [feholdexcept](feholdexcept2.md). También puede especificar el entorno de punto flotante de inicio predeterminado mediante la macro **FE_DFL_ENV** .

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si el entorno se ha establecido correctamente. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

La función **fesetenv** establece el entorno de punto flotante actual a partir del valor almacenado en el objeto **fenv_t** al que apunta *penv*. El entorno de punto flotante consiste en el conjunto de marcas de estado y modos de control que afectan a los cálculos de punto flotante. Incluye el modo de redondeo y las marcas de estado de las excepciones de punto flotante.  Si *penv* no es **FE_DFL_ENV** o no apunta a un objeto **fenv_t** válido, el comportamiento posterior es indefinido.

Una llamada a esta función establece las marcas de estado de excepción que se encuentran en el objeto *penv* , pero no genera esas excepciones.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fesetenv**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fegetenv](fegetenv1.md)<br/>
[feclearexcept](feclearexcept1.md)<br/>
[feholdexcept](feholdexcept2.md)<br/>
[fesetexceptflag](fesetexceptflag2.md)<br/>
