---
title: fegetenv
ms.date: 04/05/2018
api_name:
- fetegenv
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
- fegetenv
- fenv/fegetenv
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
ms.openlocfilehash: b2e3566eb96174d0f0ccd6beb401824cc052c995
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70941242"
---
# <a name="fegetenv"></a>fegetenv

Almacena el entorno actual de punto flotante en el objeto especificado.

## <a name="syntax"></a>Sintaxis

```C
int fegetenv(
   fenv_t *penv
);
```

### <a name="parameters"></a>Parámetros

*penv*<br/>
Puntero a un objeto **fenv_t** que contiene los valores actuales del entorno de punto flotante.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si el entorno de punto flotante se almacenó correctamente en *penv*. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

La función **fegetenv** almacena el entorno de punto flotante actual en el objeto al que apunta *penv*. El entorno de punto flotante consiste en el conjunto de marcas de estado y modos de control que afectan a los cálculos de punto flotante. Incluye el modo de dirección de redondeo y las marcas de estado de las excepciones de punto flotante.  Si *penv* no apunta a un objeto **fenv_t** válido, el comportamiento posterior es indefinido.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
