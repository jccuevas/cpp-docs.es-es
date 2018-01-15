---
title: _set_abort_behavior | Microsoft Docs
ms.custom: 
ms.date: 1/02/2018
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname: _set_abort_behavior
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
dev_langs: C++
helpviewer_keywords:
- aborting programs
- _set_abort_behavior function
- set_abort_behavior function
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 965ff160fd8098c60f53f639cb95aedf890edd86
ms.sourcegitcommit: a5d8f5b92cb5e984d5d6c9d67fe8a1241f3fe184
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/05/2018
---
# <a name="setabortbehavior"></a>_set_abort_behavior

Especifica la acción que se debe llevar a cabo cuando un programa finaliza de forma anormal.

> [!NOTE]
> No utilice la `abort` función para cerrar una aplicación de Microsoft Store, excepto en pruebas o en escenarios de depuración. No se permiten formas mediante programación o la interfaz de usuario para cerrar una aplicación de tienda según la [las directivas de Microsoft Store](http://go.microsoft.com/fwlink/?LinkId=865936). Para obtener más información, consulte [ciclo de vida de aplicación UWP](http://go.microsoft.com/fwlink/p/?LinkId=865934).

## <a name="syntax"></a>Sintaxis

```C
unsigned int _set_abort_behavior(
   unsigned int flags,
   unsigned int mask
);
```

### <a name="parameters"></a>Parámetros

[in] _marcas_  
Nuevo valor de las marcas `abort`.

[in] _máscara_  
Máscara para los bits de las marcas `abort` que se deben establecer.

## <a name="return-value"></a>Valor devuelto

Valor anterior de las marcas.

## <a name="remarks"></a>Comentarios

Hay dos marcas `abort`: `_WRITE_ABORT_MSG` y `_CALL_REPORTFAULT`. `_WRITE_ABORT_MSG` determina si se imprime un mensaje de texto de ayuda cuando un programa finaliza de forma anormal. El mensaje indica que la aplicación ha llamado a la función `abort`. El comportamiento predeterminado consiste en imprimir el mensaje. `_CALL_REPORTFAULT` (si se establece) especifica que se genera y notifica un volcado de memoria Watson cuando se llama a `abort`. De forma predeterminada, los informes de volcado de memoria están habilitados en las compilaciones que no son de DEBUG.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|`_set_abort_behavior`|\<stdlib.h>|

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

[abort](../../c-runtime-library/reference/abort.md)  
