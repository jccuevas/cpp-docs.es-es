---
title: __max
ms.date: 04/05/2018
apiname:
- __max
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
apitype: DLLExport
f1_keywords:
- max
- __max
helpviewer_keywords:
- max macro
- maximum macro
- __max macro
ms.assetid: 05c936f6-0e22-45d6-a58d-4bc102e9dae2
ms.openlocfilehash: 32e1207ea4bb030ac5303de32c0566f98e0596a3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50613764"
---
# <a name="max"></a>__max

Macro de preprocesador que devuelve el mayor de dos valores.

## <a name="syntax"></a>Sintaxis

```C
#define __max(a,b) (((a) > (b)) ? (a) : (b))
```

### <a name="parameters"></a>Parámetros

*un*, *b*<br/>
Valores de cualquier tipo numérico que se va a comparar.

## <a name="return-value"></a>Valor devuelto

**__max** devuelve el mayor de sus argumentos.

## <a name="remarks"></a>Comentarios

El **__max** macro compara dos valores y devuelve el valor del mayor. Los argumentos pueden ser de cualquier tipo de datos numérico, con o sin signo. Los argumentos y el valor devuelto deben ser del mismo tipo de datos.

El argumento devuelto se evalúa dos veces, la macro. Esto puede provocar resultados inesperados si el argumento es una expresión que se modifica su valor cuando sea evaluado, tales como `*p++`.

## <a name="requirements"></a>Requisitos

|Macro|Encabezado necesario|
|-------------|---------------------|
|**__max**|\<stdlib.h>|

## <a name="example"></a>Ejemplo

Para obtener más información, vea el ejemplo de [__min](min.md).

## <a name="see-also"></a>Vea también

[Compatibilidad con el punto flotante](../../c-runtime-library/floating-point-support.md)<br/>
[__min](min.md)<br/>