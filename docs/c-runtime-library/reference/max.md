---
title: __max
ms.date: 04/05/2018
api_name:
- __max
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
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 4cdfd99ec344cd357900d76dfc7f9400046e448a
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170194"
---
# <a name="__max"></a>__max

Macro de preprocesador que devuelve el mayor de dos valores.

## <a name="syntax"></a>Sintaxis

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parámetros

*a*, *b*<br/>
Valores de cualquier tipo numérico que se va a comparar.

## <a name="return-value"></a>Valor devuelto

**__max** devuelve el mayor de sus argumentos.

## <a name="remarks"></a>Observaciones

La macro **__max** compara dos valores y devuelve el valor de mayor. Los argumentos pueden ser de cualquier tipo de datos numérico, con o sin signo. Los argumentos y el valor devuelto deben ser del mismo tipo de datos.

La macro evalúa dos veces el argumento devuelto. Esto puede dar lugar a resultados inesperados si el argumento es una expresión que modifica su valor cuando se evalúa, como `*p++`.

## <a name="requirements"></a>Requisitos

|Macro|Encabezado necesario|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>Ejemplo

Para obtener más información, vea el ejemplo de [__min](min.md).

## <a name="see-also"></a>Consulte también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>
