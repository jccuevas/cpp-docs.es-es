---
title: _CrtSetDbgFlag
ms.date: 11/04/2016
api_name:
- _CrtSetDbgFlag
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
- _CRTDBG_REPORT_FLAG
- _CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_DEFAULT_DF
- CRTDBG_CHECK_EVERY_128_DF
- CRTDBG_CHECK_EVERY_1024_DF
- _CRTDBG_CHECK_EVERY_128_DF
- CrtSetDbgFlag
- CRTDBG_CHECK_EVERY_16_DF
- _CRTDBG_CHECK_EVERY_1024_DF
- _CrtSetDbgFlag
- CRTDBG_REPORT_FLAG
helpviewer_keywords:
- _CRTDBG_CHECK_EVERY_16_DF macro
- CRTDBG_CHECK_EVERY_16_DF macro
- _CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_ALLOC_MEM_DF macro
- CRTDBG_CHECK_ALWAYS_DF macro
- _CRTDBG_ALLOC_MEM_DF macro
- _CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_REPORT_FLAG macro
- _CRTDBG_CHECK_EVERY_1024_DF macro
- CRTDBG_CHECK_DEFAULT_DF macro
- CRTDBG_CHECK_EVERY_1024_DF macro
- _CrtSetDbgFlag function
- CrtSetDbgFlag function
- _CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_EVERY_128_DF macro
- CRTDBG_DELAY_FREE_MEM_DF macro
- CRTDBG_CHECK_CRT_DF macro
- _CRTDBG_CHECK_CRT_DF macro
ms.assetid: b5657ffb-6178-4cbf-9886-1af904ede94c
ms.openlocfilehash: 8506b593a579c8dd1791e56c320bd9d8e2ee9ba2
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938614"
---
# <a name="_crtsetdbgflag"></a>_CrtSetDbgFlag

Recupera o modifica el estado de la marca **_crtDbgFlag** para controlar el comportamiento de asignación del administrador del montón de depuración (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
int _CrtSetDbgFlag(
   int newFlag
);
```

### <a name="parameters"></a>Parámetros

*newFlag*<br/>
Nuevo estado de **_crtDbgFlag**.

## <a name="return-value"></a>Valor devuelto

Devuelve el estado anterior de **_crtDbgFlag**.

## <a name="remarks"></a>Comentarios

La función _ **crtsetdbgflag** permite que la aplicación controle cómo el administrador del montón de depuración realiza el seguimiento de las asignaciones de memoria modificando los campos de bits de la marca _ **crtdbgflag** . Mediante el establecimiento (la activación) de los bits, la aplicación puede indicar al administrador del montón de depuración que realice operaciones especiales de depuración, como por ejemplo: comprobar si existen pérdidas de memoria cuando se cierra la aplicación y notificarlas si las hay; simular condiciones de memoria insuficiente especificando que los bloques de memoria liberados permanezcan en la lista vinculada del montón; y comprobar la integridad del montón examinando cada bloque de memoria de cada solicitud de asignación. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a _ **crtsetdbgflag** se quitan durante el preprocesamiento.

En la tabla siguiente se muestran los campos de bits de **_crtDbgFlag** y se describe su comportamiento. Dado que el establecimiento de los bits da lugar a más resultados de diagnóstico y menor velocidad de ejecución del programa, estos bits no se establecen (están desactivados) de forma predeterminada. Para obtener más información sobre estos campos de bits, consulte [Funciones que indican el estado del montón](/visualstudio/debugger/crt-debug-heap-details).

|Campo de bit|Valor predeterminado|DESCRIPCIÓN|
|---------------|-------------|-----------------|
|**_CRTDBG_ALLOC_MEM_DF**|ON|EN Habilite las asignaciones del montón de depuración y el uso de identificadores de tipo de bloque de memoria, como _ **client_block**. HABILITAR Agregue nuevas asignaciones a la lista vinculada del montón, pero establezca tipo de bloque en **_IGNORE_BLOCK**.<br /><br /> También se puede combinar con cualquiera de las macros de comprobación de frecuencia del montón.|
|**_CRTDBG_CHECK_ALWAYS_DF**|OFF|EN Llame a [_CrtCheckMemory](crtcheckmemory.md) en cada solicitud de asignación y desasignación. OFF: se debe llamar a **_CrtCheckMemory** explícitamente.<br /><br /> Las macros de comprobación de la frecuencia del montón no tienen ningún efecto cuando esta marca está establecida.|
|**_CRTDBG_CHECK_CRT_DF**|OFF|EN Incluir tipos _ **crt_block** en operaciones de detección de pérdidas y de diferencia de estado de memoria. HABILITAR Estas operaciones omiten la memoria que usa internamente la biblioteca en tiempo de ejecución.<br /><br /> También se puede combinar con cualquiera de las macros de comprobación de frecuencia del montón.|
|**_CRTDBG_DELAY_FREE_MEM_DF**|OFF|EN Mantenga los bloques de memoria liberados en la lista vinculada del montón, asígneles el tipo **_FREE_BLOCK** y rellénelo con el valor de byte 0xDD. HABILITAR No mantenga los bloques liberados en la lista vinculada del montón.<br /><br /> También se puede combinar con cualquiera de las macros de comprobación de frecuencia del montón.|
|**_CRTDBG_LEAK_CHECK_DF**|OFF|EN Realizar la comprobación automática de pérdidas al salir del programa a través de una llamada a _ [crtdumpmemoryleaks](crtdumpmemoryleaks.md) y generar un informe de errores si la aplicación no pudo liberar toda la memoria asignada. HABILITAR No realice automáticamente la comprobación de pérdidas al salir del programa.<br /><br /> También se puede combinar con cualquiera de las macros de comprobación de frecuencia del montón.|

**Macros de frecuencia de comprobación del montón**

Puede especificar la frecuencia con la que la biblioteca en tiempo de ejecución de C realiza la validación del montón de depuración ( **_CrtCheckMemory**) en función del número de llamadas a **malloc**, **realloc**, **Free**y **_msize**.

_ **Crtsetdbgflag** inspecciona los 16 bits superiores del parámetro *newFlag* para un valor. El valor especificado es el número de llamadas a **malloc**, **realloc**, **Free**y **_msize** entre llamadas a **_CrtCheckMemory** . Hay cuatro macros predefinidas para hacerlo.

|Macro|Número de llamadas a malloc, realloc, free y _msize entre llamadas a _CrtCheckMemory|
|-----------|------------------------------------------------------------------------------------------|
|_CRTDBG_CHECK_EVERY_16_DF|16|
|_CRTDBG_CHECK_EVERY_128_DF|128|
|_CRTDBG_CHECK_EVERY_1024_DF|1024|
|_CRTDBG_CHECK_DEFAULT_DF|0 (de forma predeterminada, no se comprueba el montón)|

De forma predeterminada, se llama a **_CrtCheckMemory** una vez cada 1.024 veces que se llama a **malloc**, **realloc**, **Free**y **_msize**.

Por ejemplo, puede especificar una comprobación del montón cada 16 operaciones **malloc**, **realloc**, **Free**y **_msize** con el código siguiente:

```C
#include <crtdbg.h>
int main( )
{
    int tmp;

    // Get the current bits
    tmp = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);

    // Clear the upper 16 bits and OR in the desired frequency
    tmp = (tmp & 0x0000FFFF) | _CRTDBG_CHECK_EVERY_16_DF;

    // Set the new bits
    _CrtSetDbgFlag(tmp);
}
```

Los 16 bits superiores del parámetro *newFlag* se omiten cuando se especifica _CRTDBG_CHECK_ALWAYS_DF. En este caso, se llama a **_CrtCheckMemory** cada vez que se llama a **malloc**, **realloc**, **Free**y **_msize**.

*newFlag* es el nuevo estado que se debe aplicar a _ **crtdbgflag** y es una combinación de los valores de cada uno de los campos de bits.

### <a name="to-change-one-or-more-of-these-bit-fields-and-create-a-new-state-for-the-flag"></a>Para cambiar estos campos de bits y crear un nuevo estado para la marca

1. Llame a _ **crtsetdbgflag** con *NewFlag* igual a **_CRTDBG_REPORT_FLAG** para obtener el estado de _ **crtdbgflag** actual y almacenar el valor devuelto en una variable temporal.

1. Active los bits mediante **una operación OR bit a bit** de la variable temporal con la máscara de bits correspondiente (representada en el código de aplicación mediante constantes de manifiesto).

1. Desactive los demás bits realizando la operación **AND** a la variable con un **NOT** bit a bit de las máscaras de bits adecuadas.

1. Llame a _ **crtsetdbgflag** con *newFlag* igual al valor almacenado en la variable temporal para establecer el nuevo estado de _ **crtdbgflag**.

En el código siguiente se muestra cómo simular condiciones de memoria insuficiente conservando los bloques de memoria liberados en la lista vinculada del montón y evitar que se llame a **_CrtCheckMemory** en cada solicitud de asignación:

```C
// Get the current state of the flag
// and store it in a temporary variable
int tmpFlag = _CrtSetDbgFlag( _CRTDBG_REPORT_FLAG );

// Turn On (OR) - Keep freed memory blocks in the
// heap's linked list and mark them as freed
tmpFlag |= _CRTDBG_DELAY_FREE_MEM_DF;

// Turn Off (AND) - prevent _CrtCheckMemory from
// being called at every allocation request
tmpFlag &= ~_CRTDBG_CHECK_ALWAYS_DF;

// Set the new state for the flag
_CrtSetDbgFlag( tmpFlag );
```

Para obtener información general sobre la administración de memoria y el montón de depuración, consulte [Detalles del montón de depuración de CRT](/visualstudio/debugger/crt-debug-heap-details).

Para deshabilitar una marca con la función _ **crtsetdbgflag** , debe **y** la variable con el **operador bit** a bit de la máscara de bits.

Si *newFlag* no es un valor válido, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno** en **EINVAL** y devuelve el estado anterior de _ **crtdbgflag**.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtSetDbgFlag**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="example"></a>Ejemplo

```C
// crt_crtsetdflag.c
// compile with: /c -D_DEBUG /MTd -Od -Zi -W3 /link -verbose:lib /debug

// This program concentrates on allocating and freeing memory
// blocks to test the functionality of the _crtDbgFlag flag.

#include <string.h>
#include <malloc.h>
#include <crtdbg.h>

int main( )
{
    char *p1, *p2;
    int tmpDbgFlag;

    _CrtSetReportMode( _CRT_ERROR, _CRTDBG_MODE_FILE );
    _CrtSetReportFile( _CRT_ERROR, _CRTDBG_FILE_STDERR );

    // Set the debug-heap flag to keep freed blocks in the
    // heap's linked list - This will allow us to catch any
    // inadvertent use of freed memory
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_DELAY_FREE_MEM_DF;
    tmpDbgFlag |= _CRTDBG_LEAK_CHECK_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Allocate 2 memory blocks and store a string in each
    p1 = malloc( 34 );
    p2 = malloc( 38 );
    strcpy_s( p1, 34, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 38, "p2 points to a Client allocation block" );

    // Free both memory blocks
    free( p2 );
    free( p1 );

    // Set the debug-heap flag to no longer keep freed blocks in the
    // heap's linked list and turn on Debug type allocations (CLIENT)
    tmpDbgFlag = _CrtSetDbgFlag(_CRTDBG_REPORT_FLAG);
    tmpDbgFlag |= _CRTDBG_ALLOC_MEM_DF;
    tmpDbgFlag &= ~_CRTDBG_DELAY_FREE_MEM_DF;
    _CrtSetDbgFlag(tmpDbgFlag);

    // Explicitly call _malloc_dbg to obtain the filename and
    // line number of our allocation request and also so we can
    // allocate CLIENT type blocks specifically for tracking
    p1 = _malloc_dbg( 40, _NORMAL_BLOCK, __FILE__, __LINE__ );
    p2 = _malloc_dbg( 40, _CLIENT_BLOCK, __FILE__, __LINE__ );
    strcpy_s( p1, 40, "p1 points to a Normal allocation block" );
    strcpy_s( p2, 40, "p2 points to a Client allocation block" );

    // _free_dbg must be called to free the CLIENT block
    _free_dbg( p2, _CLIENT_BLOCK );
    free( p1 );

    // Allocate p1 again and then exit - this will leave unfreed
    // memory on the heap
    p1 = malloc( 10 );
}
```

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_crtDbgFlag](../../c-runtime-library/crtdbgflag.md)<br/>
[_CrtCheckMemory](crtcheckmemory.md)<br/>
