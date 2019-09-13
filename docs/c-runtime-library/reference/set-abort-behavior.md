---
title: _set_abort_behavior
ms.date: 01/02/2018
apiname:
- _set_abort_behavior
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
- _set_abort_behavior
- set_abort_behavior
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
ms.openlocfilehash: b72a485287684fc85f1e232e89774e07a5e3f42b
ms.sourcegitcommit: effb516760c0f956c6308eeded48851accc96b92
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70927487"
---
# <a name="_set_abort_behavior"></a>_set_abort_behavior

Especifica la acción que se debe llevar a cabo cuando un programa finaliza de forma anormal.

> [!NOTE]
> No use la función [Abort](abort.md) para cerrar una Microsoft Store aplicación, excepto en escenarios de prueba o depuración. No se permiten las formas de cerrar una aplicación de la tienda mediante programación o la interfaz de usuario de acuerdo con las [directivas de Microsoft Store](/legal/windows/agreements/store-policies). Para obtener más información, consulte el ciclo de vida de las [aplicaciones para UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Sintaxis

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parámetros

*flags*<br/>
Nuevo valor de las marcas de [anulación](abort.md) .

*mask*<br/>
Máscara de los bits de las marcas de [anulación](abort.md) que se van a establecer.

## <a name="return-value"></a>Valor devuelto

Valor anterior de las marcas.

## <a name="remarks"></a>Comentarios

Hay dos marcas de [anulación](abort.md) : **_WRITE_ABORT_MSG** y **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** determina si se imprime un mensaje de texto útil cuando un programa finaliza de forma anómala. El mensaje indica que la aplicación ha llamado a la función [Abort](abort.md) . El comportamiento predeterminado consiste en imprimir el mensaje. **_CALL_REPORTFAULT**, si se establece, especifica que se genera un volcado de memoria de Watson y se indica cuando se llama a [Abort](abort.md) . De forma predeterminada, los informes de volcado de memoria están habilitados en las compilaciones que no son de DEBUG.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_set_abort_behavior**|\<stdlib.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

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

## <a name="see-also"></a>Vea también

[abort](abort.md)<br/>
