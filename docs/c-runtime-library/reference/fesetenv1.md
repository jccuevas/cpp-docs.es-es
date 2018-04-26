---
title: fesetenv | Documentos de Microsoft
ms.custom: ''
ms.date: 04/05/2018
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp
- devlang-cpp
ms.tgt_pltfrm: ''
ms.topic: reference
apiname:
- fesetenv
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- fesetenv
- fenv/fesetenv
dev_langs:
- C++
helpviewer_keywords:
- fesetenv function
ms.assetid: ffc64fff-8ea7-4d59-9e04-ff96ef8cd012
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 466d37a55cbd0d4fdf3e1fc0eed085cb9fcb5b6a
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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
Puntero a un **fenv_t** objeto que contiene un entorno de punto flotante como conjunto mediante una llamada a [fegetenv](fegetenv1.md) o [feholdexcept](feholdexcept2.md). También puede especificar el entorno de punto flotante de inicio predeterminado mediante el **FE_DFL_ENV** macro.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si el entorno se ha establecido correctamente. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

El **fesetenv** función establece el entorno de punto flotante actual desde el valor almacenado en el **fenv_t** objeto señalado por *penv*. El entorno de punto flotante consiste en el conjunto de marcas de estado y modos de control que afectan a los cálculos de punto flotante. Incluye el modo de redondeo y las marcas de estado de las excepciones de punto flotante.  Si *penv* no **FE_DFL_ENV** o no apunta a válido **fenv_t** objeto posterior comportamiento es indefinido.

Una llamada a esta función establece la excepción de los indicadores de estado que se encuentran en el *penv* objeto, pero no genera esas excepciones.

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
