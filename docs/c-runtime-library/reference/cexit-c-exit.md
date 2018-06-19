---
title: _cexit, _c_exit | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _c_exit
- _cexit
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
- _cexit
- c_exit
- _c_exit
- cexit
dev_langs:
- C++
helpviewer_keywords:
- cleanup operations during processes
- cexit function
- _c_exit function
- _cexit function
- c_exit function
ms.assetid: f3072045-9924-4b1a-9fef-b0dcd6d12663
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b0840ccec85d46a13984b65ebe99e53b968bedeb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
ms.locfileid: "32395827"
---
# <a name="cexit-cexit"></a>_cexit, _c_exit

Realiza operaciones de limpieza y vuelve sin finalizar el proceso.

## <a name="syntax"></a>Sintaxis

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Comentarios

El **_cexit** llamadas a funciones, en el último en entrar en orden de salir (LIFO), las funciones registradas por **atexit** y **_onexit**. A continuación, **_cexit** vacía todos los búferes de E/S y cierra todas las secuencias abiertas antes de devolver. **_c_exit** es el mismo que **_exit** pero devuelve al proceso que realiza la llamada sin procesar **atexit** o **_onexit** o vaciar los búferes de secuencia. El comportamiento de **salir**, **_exit**, **_cexit**, y **_c_exit** se muestra en la tabla siguiente.

|Función|Comportamiento|
|--------------|--------------|
|**exit**|Realiza los procedimientos completos de finalización de la biblioteca de C, finaliza el proceso y se cierra con el código de estado especificado.|
|**_exit**|Realiza los procedimientos rápidos de finalización de la biblioteca de C, finaliza el proceso y se cierra con el código de estado especificado.|
|**_cexit**|Realiza procedimientos completos de finalización de la biblioteca de C y vuelve al autor de la llamada, pero no finaliza el proceso.|
|**_c_exit**|Realiza procedimientos rápidos de finalización de la biblioteca de C y vuelve al autor de la llamada, pero no finaliza el proceso.|

Cuando se llama a la **_cexit** o **_c_exit** funciones, no se llaman a los destructores de ningún objeto temporal o automático que exista en el momento de la llamada. Un objeto automático es el que se define en una función en la que el objeto no se declara como estático. Un objeto temporal es el que crea el compilador. Para destruir un objeto automático antes de llamar a **_cexit** o **_c_exit**, explícitamente llama al destructor del objeto, como se indica a continuación:

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
