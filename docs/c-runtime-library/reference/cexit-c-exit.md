---
title: _cexit, _c_exit
ms.date: 11/04/2016
api_name:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
ms.openlocfilehash: aa25d73bef1d85adfed77ba926e2d381e02e45e8
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70939251"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Realiza operaciones de limpieza y vuelve sin finalizar el proceso.

## <a name="syntax"></a>Sintaxis

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Comentarios

La función **_cexit** llama a, en orden LIFO (último en salir, primero en salir), las funciones registradas por **AtExit** y **_onexit**. Después, **_cexit** vacía todos los búferes de e/s y cierra todas las transmisiones abiertas antes de volver. **_c_exit** es igual que **_exit** , pero vuelve al proceso que realiza la llamada sin procesar **AtExit** ni **_onexit** ni vaciar los búferes de secuencia. En la tabla siguiente se muestra el comportamiento de **Exit**, **_exit**, **_cexit**y **_c_exit** .

|Función|Comportamiento|
|--------------|--------------|
|**exit**|Realiza los procedimientos completos de finalización de la biblioteca de C, finaliza el proceso y se cierra con el código de estado especificado.|
|**_exit**|Realiza los procedimientos rápidos de finalización de la biblioteca de C, finaliza el proceso y se cierra con el código de estado especificado.|
|**_cexit**|Realiza procedimientos completos de finalización de la biblioteca de C y vuelve al autor de la llamada, pero no finaliza el proceso.|
|**_c_exit**|Realiza procedimientos rápidos de finalización de la biblioteca de C y vuelve al autor de la llamada, pero no finaliza el proceso.|

Cuando se llama a las funciones **_cexit** o **_c_exit** , no se llama a los destructores de ningún objeto temporal o automático que exista en el momento de la llamada. Un objeto automático es el que se define en una función en la que el objeto no se declara como estático. Un objeto temporal es el que crea el compilador. Para destruir un objeto automático antes de llamar a **_cexit** o **_c_exit**, llame explícitamente al destructor del objeto, como se indica a continuación:

```cpp
myObject.myClass::~myClass( );
```

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec (funciones)](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, _wspawn (funciones)](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
