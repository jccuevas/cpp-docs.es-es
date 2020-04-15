---
title: _set_abort_behavior
ms.date: 4/2/2020
api_name:
- _set_abort_behavior
- _o__set_abort_behavior
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: fd3a3c2f99d1702cdccf68328c2122b965b2d078
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81337870"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

Especifica la acción que se debe llevar a cabo cuando un programa finaliza de forma anormal.

> [!NOTE]
> No use la función [de anulación](abort.md) para apagar una aplicación de Microsoft Store, excepto en escenarios de prueba o depuración. No se permiten formas de uso mediante programación o de interfaz de usuario para cerrar una aplicación de la Tienda de acuerdo con las directivas de [Microsoft Store.](/legal/windows/agreements/store-policies) Para obtener más información, consulta Ciclo de vida de la [aplicación para UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Sintaxis

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parámetros

*Banderas*<br/>
Nuevo valor de los indicadores [abort.](abort.md)

*Máscara*<br/>
Máscara para los bits de las marcas [de anulación](abort.md) que se han establecido.

## <a name="return-value"></a>Valor devuelto

Valor anterior de las marcas.

## <a name="remarks"></a>Observaciones

Hay dos indicadores [abort:](abort.md) **_WRITE_ABORT_MSG** y **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** determina si se imprime un mensaje de texto útil cuando un programa finaliza anormalmente. El mensaje indica que la aplicación ha llamado a la función [de anulación.](abort.md) El comportamiento predeterminado consiste en imprimir el mensaje. **_CALL_REPORTFAULT**, si se establece, especifica que se genera un volcado de memoria de Watson y se notifica cuando se llama a [la anulación.](abort.md) De forma predeterminada, los informes de volcado de memoria están habilitados en las compilaciones que no son de DEBUG.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_set_abort_behavior.c
// compile with: /TC
#include <stdlib.h>

int main()
{
   printf("Suppressing the abort message. If successful, this message"
          " will be the only output.\n");
   // Suppress the abort message
   _set_abort_behavior( 0, _WRITE_ABORT_MSG);
   abort();
}
```

```Output
Suppressing the abort message. If successful, this message will be the only output.
```

## <a name="see-also"></a>Consulte también

[Aborta](abort.md)<br/>
