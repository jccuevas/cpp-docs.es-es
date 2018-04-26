---
title: fegetenv | Documentos de Microsoft
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
- fetegenv
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
- fegetenv
- fenv/fegetenv
dev_langs:
- C++
helpviewer_keywords:
- fetegenv function
ms.assetid: 68962421-6978-4b27-8e4c-ad1577830cf6
caps.latest.revision: 7
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: a3569b015784f41fae4a4a91b6a32fe08dd57284
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
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
Puntero a un **fenv_t** objeto que contiene los valores de punto flotante del entorno actual.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si el entorno de punto flotante se almacenó correctamente en *penv*. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

El **fegetenv** función almacena el entorno de punto flotante actual en el objeto al que señala *penv*. El entorno de punto flotante consiste en el conjunto de marcas de estado y modos de control que afectan a los cálculos de punto flotante. Incluye el modo de dirección de redondeo y las marcas de estado de las excepciones de punto flotante.  Si *penv* no apunta a válido **fenv_t** objeto posterior comportamiento es indefinido.

Para usar esta función, debe desactivar las optimizaciones de punto flotante que podrían impedir el acceso mediante la directiva `#pragma fenv_access(on)` antes de la llamada. Para obtener más información, consulta [fenv_access](../../preprocessor/fenv-access.md).

## <a name="requirements"></a>Requisitos

|Función|Encabezado C|Encabezado C++|
|--------------|--------------|------------------|
|**fegetenv**|\<fenv.h>|\<cfenv>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Referencia alfabética de funciones](crt-alphabetical-function-reference.md)<br/>
[fesetenv](fesetenv1.md)<br/>
