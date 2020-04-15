---
title: _cexit, _c_exit
ms.date: 4/2/2020
api_name:
- _c_exit
- _cexit
- _o__cexit
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
ms.openlocfilehash: 9eb856efca054423465aa7d30092edaf83a65eeb
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333531"
---
# <a name="_cexit-_c_exit"></a>_cexit, _c_exit

Realiza operaciones de limpieza y vuelve sin finalizar el proceso.

## <a name="syntax"></a>Sintaxis

```C
void _cexit( void );
void _c_exit( void );
```

## <a name="remarks"></a>Observaciones

La **función _cexit** llama, en orden de último en entrar, primero en salir (LIFO), las funciones registradas por **atexit** y **_onexit**. A continuación, **_cexit** vacía todos los búferes de E/S y cierra todas las secuencias abiertas antes de volver. **_c_exit** es lo mismo que **_exit** pero vuelve al proceso de llamada sin procesar los búferes de flujo **de _onexit** o **de** vaciado. El comportamiento de **exit**, **_exit**, **_cexit**y **_c_exit** se muestra en la tabla siguiente.

|Función|Comportamiento|
|--------------|--------------|
|**Salida**|Realiza los procedimientos completos de finalización de la biblioteca de C, finaliza el proceso y se cierra con el código de estado especificado.|
|**_exit**|Realiza los procedimientos rápidos de finalización de la biblioteca de C, finaliza el proceso y se cierra con el código de estado especificado.|
|**_cexit**|Realiza procedimientos completos de finalización de la biblioteca de C y vuelve al autor de la llamada, pero no finaliza el proceso.|
|**_c_exit**|Realiza procedimientos rápidos de finalización de la biblioteca de C y vuelve al autor de la llamada, pero no finaliza el proceso.|

Cuando se llama a las **funciones _cexit** o **_c_exit,** no se llama a los destructores de los objetos temporales o automáticos que existen en el momento de la llamada. Un objeto automático es el que se define en una función en la que el objeto no se declara como estático. Un objeto temporal es el que crea el compilador. Para destruir un objeto automático antes de llamar a **_cexit** o **_c_exit**, llame explícitamente al destructor del objeto, como se indica a continuación:

```cpp
myObject.myClass::~myClass( );
```

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_cexit**|\<process.h>|
|**_c_exit**|\<process.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulte también

[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[Aborta](abort.md)<br/>
[atexit](atexit.md)<br/>
[_exec, _wexec funciones](../../c-runtime-library/exec-wexec-functions.md)<br/>
[exit, _Exit, _exit](exit-exit-exit.md)<br/>
[_onexit, _onexit_m](onexit-onexit-m.md)<br/>
[_spawn, funciones _wspawn](../../c-runtime-library/spawn-wspawn-functions.md)<br/>
[system, _wsystem](system-wsystem.md)<br/>
