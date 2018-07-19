---
title: _set_abort_behavior | Microsoft Docs
ms.custom: ''
ms.date: 1/02/2018
ms.technology:
- cpp-standard-libraries
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: fb308e527cc955d91af0b12547d52aa5e6316af5
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32407280"
---
# <a name="setabortbehavior"></a>_set_abort_behavior

Especifica la acción que se debe llevar a cabo cuando un programa finaliza de forma anormal.

> [!NOTE]
> No utilice la [anular](abort.md) función para cerrar una aplicación de Microsoft Store, excepto en pruebas o en escenarios de depuración. No se permiten formas mediante programación o la interfaz de usuario para cerrar una aplicación de tienda según la [las directivas de Microsoft Store](http://go.microsoft.com/fwlink/?LinkId=865936). Para obtener más información, consulte [ciclo de vida de aplicación UWP](http://go.microsoft.com/fwlink/p/?LinkId=865934).

## <a name="syntax"></a>Sintaxis

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parámetros

*flags*<br/>
Nuevo valor de la [anular](abort.md) marcas.

*máscara*<br/>
Máscara para la [anular](abort.md) marcas de bits para establecer.

## <a name="return-value"></a>Valor devuelto

Valor anterior de las marcas.

## <a name="remarks"></a>Comentarios

Hay dos [anular](abort.md) marcas: **_WRITE_ABORT_MSG** y **_CALL_REPORTFAULT**. **_WRITE_ABORT_MSG** determina si se imprime un mensaje de texto de ayuda cuando un programa se termina de forma anómala. El mensaje indica que la aplicación ha llamado el [anular](abort.md) función. El comportamiento predeterminado consiste en imprimir el mensaje. **_CALL_REPORTFAULT**, si se establece, especifica que un volcado de Watson se genera y notifica cuando [anular](abort.md) se llama. De forma predeterminada, los informes de volcado de memoria están habilitados en las compilaciones que no son de DEBUG.

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
