---
title: _configthreadlocale
ms.date: 4/2/2020
api_name:
- _configthreadlocale
- _o__configthreadlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- _configthreadlocale
- configthreadlocale
helpviewer_keywords:
- configthreadlocale function
- locales, per-thread
- _configthreadlocale function
- per-thread locale
- thread locale
ms.assetid: 10e4050e-b587-4f30-80bc-6c76b35fc770
ms.openlocfilehash: 46983843e128b59df89722c8d4694c30a858011f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81348538"
---
# <a name="_configthreadlocale"></a>_configthreadlocale

Configurar las opciones de configuración regional por subproceso.

## <a name="syntax"></a>Sintaxis

```C
int _configthreadlocale( int per_thread_locale_type );
```

### <a name="parameters"></a>Parámetros

*per_thread_locale_type*<br/>
Opción que se va a establecer. Una de las opciones que se citan en la tabla siguiente.

## <a name="return-value"></a>Valor devuelto

El estado de configuración regional por subproceso anterior **(_DISABLE_PER_THREAD_LOCALE** o **_ENABLE_PER_THREAD_LOCALE**) o -1 en caso de error.

## <a name="remarks"></a>Observaciones

La función **_configurethreadlocale** se utiliza para controlar el uso de configuraciones regionales específicas de subprocesos. Utilice una de estas *opciones de per_thread_locale_type* para especificar o determinar el estado de configuración regional por subproceso:

| Opción | Descripción |
|-|-|
| **_ENABLE_PER_THREAD_LOCALE** | Hace que el subproceso actual use una configuración regional específica del subproceso. Las llamadas posteriores a **setlocale** en este subproceso solo afectan a la propia configuración regional del subproceso. |
| **_DISABLE_PER_THREAD_LOCALE** | Hace que el subproceso actual use la configuración regional global. Las llamadas posteriores a **setlocale** en este subproceso afectan a otros subprocesos mediante la configuración regional global. |
| **0** | Recupera el valor actual de este subproceso concreto. |

Estas funciones afectan al comportamiento de **setlocale**, **_tsetlocale**, **_wsetlocale**y **_setmbcp**. Cuando se deshabilita la configuración regional por subproceso, cualquier llamada posterior a **setlocale** o **_wsetlocale** cambia la configuración regional de todos los subprocesos que usan la configuración regional global. Cuando la configuración regional por subproceso está habilitada, **setlocale** o **_wsetlocale** solo afecta a la configuración regional del subproceso actual.

Si usa **_configurethreadlocale** para habilitar una configuración regional por subproceso, se recomienda llamar a **setlocale** o **_wsetlocale** establecer la configuración regional preferida en ese subproceso inmediatamente después.

Si *per_thread_locale_type* no es uno de los valores enumerados en la tabla, esta función invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, esta función establece **errno en** **EINVAL** y devuelve -1.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_configthreadlocale**|\<locale.h>|

## <a name="example"></a>Ejemplo

```cpp
// crt_configthreadlocale.cpp
//
// This program demonstrates the use of _configthreadlocale when
// using two independent threads.
//
// Compile by using: cl /EHsc /W4 crt_configthreadlocale.cpp

#include <locale.h>
#include <mbctype.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date and time in the current
// locale's format.
int get_time(unsigned char* str)
{
    __time64_t  ltime;
    struct tm   thetime;

    // Retieve the time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // using %#x is the long date representation,
    // appropriate to the current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm*)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to German
// and prints the time.
unsigned __stdcall SecondThreadFunc( void* /*pArguments*/ )
{
    unsigned char str[BUFF_SIZE];

    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the thread code page
    _setmbcp(_MB_CP_ANSI);

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "German"));

    // Retrieve the time string from the helper function
    if (get_time(str) == 0)
    {
        printf("The time in German locale is: '%s'\n", str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread spawns a second thread (above) and then
// sets the locale to English and prints the time.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Retrieve the time string from the helper function
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "English"));

    // Create the second thread.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      NULL, 0, &threadID );

    if (get_time(str) == 0)
    {
        // Retrieve the time string from the helper function
        printf("The time in English locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to English_United States.1252.
The time in English locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to German_Germany.1252.
The time in German locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>Consulte también

[setlocale, _wsetlocale](setlocale-wsetlocale.md)<br/>
[_beginthread, _beginthreadex](beginthread-beginthreadex.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[Multithreading y Locales](../../parallel/multithreading-and-locales.md)<br/>
