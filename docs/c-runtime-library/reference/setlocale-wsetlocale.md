---
title: setlocale, _wsetlocale
ms.date: 11/04/2016
apiname:
- _wsetlocale
- setlocale
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
- api-ms-win-crt-locale-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _wsetlocale
- _tsetlocale
- setlocale
helpviewer_keywords:
- wsetlocale function
- setlocale function
- tsetlocale function
- locales, defining
- _tsetlocale function
- defining locales
- _wsetlocale function
ms.assetid: 3ffb684e-5990-4202-9553-b5339af9520d
ms.openlocfilehash: 0f2c0478ba5898ab369a04362734891f6d45cf42
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50548544"
---
# <a name="setlocale-wsetlocale"></a>setlocale, _wsetlocale

Establece o recupera la configuración regional en tiempo de ejecución.

## <a name="syntax"></a>Sintaxis

```C
char *setlocale(
   int category,
   const char *locale
);
wchar_t *_wsetlocale(
   int category,
   const wchar_t *locale
);
```

### <a name="parameters"></a>Parámetros

*category*<br/>
Categoría afectada por la configuración regional.

*locale*<br/>
Especificador de la configuración regional.

## <a name="return-value"></a>Valor devuelto

Si es válido *configuración regional* y *categoría* reciben, devuelve un puntero a la cadena asociada con los valores especificados *configuración regional* y *categoría*. Si el *configuración regional* o *categoría* no es válido, se devuelve un puntero nulo y la configuración regional actual del programa no cambian.

Por ejemplo, la llamada

```C
setlocale( LC_ALL, "en-US" );
```

establece todas las categorías y devuelve solo la cadena

```Output
en-US
```

Puede copiar la cadena devuelta por **setlocale** para restaurar esa parte de la información de configuración regional del programa. Almacenamiento local de subprocesos o global se utiliza para la cadena devuelta por **setlocale**. Las llamadas posteriores a **setlocale** sobrescriben la cadena, lo que invalida los punteros de cadena devueltos por llamadas anteriores.

## <a name="remarks"></a>Comentarios

Use la **setlocale** función para establecer, cambiar o consultar parte o toda la información de configuración regional actual de programa especificada por *configuración regional* y *categoría*. *configuración regional* hace referencia a la localidad (país o región e idioma) para el que se pueden personalizar algunos aspectos del programa. Entre las categorías dependientes de la configuración regional se encuentran el formato de fechas y el formato de presentación de valores de moneda. Si establece *configuración regional* en la cadena predeterminada para un idioma que tiene varios formatos admitidos en el equipo, debe comprobar la **setlocale** un valor devuelto para ver qué idioma se está en vigor. Por ejemplo, si establece *configuración regional* en "chino", el valor devuelto podría ser "chino simplificado" o "chino tradicional".

**_wsetlocale** es una versión con caracteres anchos de **setlocale**; el *configuración regional* argumento y el valor devuelto de **_wsetlocale** son cadenas de caracteres anchos. **_wsetlocale** y **setlocale** se comportan exactamente igual.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

El *categoría* argumento especifica las partes de información de configuración regional de un programa que se ven afectadas. Las macros utilizadas para *categoría* y las partes del programa que afecten a son los siguientes:

|*categoría* marca|Afecta a|
|-|-|
**LC_ALL**|Todas las categorías, como se indica a continuación.
**LC_COLLATE**|El **strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_ strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**, y **wcsxfrm** funciones.
**LC_CTYPE**|Las funciones de control de caracteres (excepto **isdigit**, **isxdigit**, **mbstowcs**, y **mbtowc**, que se ven afectados).
**LC_MONETARY**|Información de formato de moneda devuelta por la **localeconv** función.
**LC_NUMERIC**|Carácter para las rutinas de salida con formato de separador decimal (como **printf**), para las rutinas de conversión de datos y para la información de formato no monetaria devuelta por **localeconv**. Además del carácter del separador decimal, **LC_NUMERIC** separador de miles de conjuntos y el control de agrupación cadena devuelta por [localeconv](localeconv.md).
**LC_TIME**|El **strftime** y **wcsftime** funciones.

Esta función valida el parámetro de categoría. Si el parámetro de categoría no es ninguno de los valores especificados en la tabla anterior, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece **errno** a **EINVAL** y devuelve **NULL**.

El *configuración regional* argumento es un puntero a una cadena que especifica la configuración regional. Para obtener información acerca del formato de la *configuración regional* argumento, vea [nombres de configuración regional, idiomas y cadenas de país o región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). Si *locale* señala a una cadena vacía, la configuración regional es el entorno nativo definido por la implementación. Un valor de **C** especifica el entorno compatible con ANSI mínimo para la traducción de C. El **C** configuración regional se da por supuesto que todos los **char** tipos de datos son de 1 byte y que su valor siempre es menor que 256.

Durante el inicio del programa, se ejecuta el equivalente de la instrucción siguiente:

`setlocale( LC_ALL, "C" );`

El *configuración regional* argumento puede tomar un nombre de la configuración regional, una cadena de idioma, una cadena de idioma y el código de país o región, una página de códigos, o una cadena de lenguaje, código de país o región y página de códigos. El conjunto de nombres de configuración regional, idiomas, códigos de país o región y páginas de códigos disponibles contiene todos los admitidos por la API NLS de Windows, excepto las páginas de códigos que requieren más de dos bytes por carácter, como UTF-7 y UTF-8. Si proporciona un valor de la página de códigos de UTF-7 o UTF-8, **setlocale** producirá y devolverá **NULL**. El conjunto de nombres de configuración regional admitidos por **setlocale** se describen en [nombres de configuración regional, idiomas y cadenas de país o región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md). El conjunto de cadenas de idioma y país o región compatibles con **setlocale** aparecen en [cadenas de idioma](../../c-runtime-library/language-strings.md) y [Country/Region Strings](../../c-runtime-library/country-region-strings.md). Se recomienda emplear el formato del nombre de la configuración regional para mejorar el rendimiento y simplificar el mantenimiento de las cadenas de configuración regional insertadas en código o serializadas en el almacenamiento. Es menos probable que una actualización del sistema operativo cambie las cadenas de nombre de configuración regional que el formato de nombre de idioma y de país o región.

Un puntero null que se pasa como el *configuración regional* argumento dice **setlocale** para consultar en lugar de establecer el entorno internacional. Si el *configuración regional* argumento es un puntero nulo, no se cambia el valor de configuración regional actual del programa. En su lugar, **setlocale** devuelve un puntero a la cadena que está asociada el *categoría* de configuración regional del subproceso. Si el *categoría* argumento es **LC_ALL**, la función devuelve una cadena que indica el valor actual de cada categoría, separadas por punto y coma. Por ejemplo, la secuencia de llamadas

```C
// Set all categories and return "en-US"
setlocale(LC_ALL, "en-US");
// Set only the LC_MONETARY category and return "fr-FR"
setlocale(LC_MONETARY, "fr-FR");
printf("%s\n", setlocale(LC_ALL, NULL));
```

devuelve

```Output
LC_COLLATE=en-US;LC_CTYPE=en-US;LC_MONETARY=fr-FR;LC_NUMERIC=en-US;LC_TIME=en-US
```

que es la cadena que está asociada el **LC_ALL** categoría.

Los ejemplos siguientes corresponden a la **LC_ALL** categoría. Se puede usar la cadena ".OCP" o la cadena ".ACP" en lugar de un número de página de códigos para especificar que se usen la página de códigos OEM predeterminada del usuario y la página de códigos ANSI predeterminada del usuario, respectivamente.

- `setlocale( LC_ALL, "" );`

   Establece la configuración regional en el valor predeterminado, que es la página de códigos ANSI predeterminada del usuario obtenida del sistema operativo.

- `setlocale( LC_ALL, ".OCP" );`

   Establece explícitamente la configuración regional en la página de códigos OEM actual obtenida del sistema operativo.

- `setlocale( LC_ALL, ".ACP" );`

   Establece la configuración regional en la página de códigos ANSI obtenida del sistema operativo.

- `setlocale( LC_ALL, "<localename>" );`

   Establece la configuración regional en el nombre de configuración regional que se indica en *\<localename>*.

- `setlocale( LC_ALL, "<language>_<country>" );`

   Establece la configuración regional en el idioma y el país o región indicados por *\<language>* y *\<country>*, junto con la página de códigos predeterminada obtenida del sistema operativo host.

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Establece la configuración regional del idioma, país o región, y página de códigos indicada por el  *\<lenguaje >*,  *\<país >*, y  *\<página_de_códigos >* cadenas. Puede utilizar distintas combinaciones de idioma, país o región y página de códigos. Por ejemplo, esta llamada establece la configuración regional en francés de Canadá con la página de códigos 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Esta llamada establece la configuración regional en francés de Canadá con la página de códigos ANSI predeterminada:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Esta llamada establece la configuración regional en francés de Canadá con la página de códigos OEM predeterminada:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Establece la configuración regional en el idioma que se indica mediante *\<language>*, y utiliza el país o región predeterminados para el idioma especificado, además de la página de códigos ANSI predeterminada del usuario para ese país o región, tal y como se obtiene del sistema operativo del host. Por ejemplo, las siguientes llamadas a **setlocale** son funcionalmente equivalentes:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Se recomienda usar el primer formato para mejorar el rendimiento y el mantenimiento.

- `setlocale( LC_ALL, ".<code_page>" );`

   Establece la página de códigos en el valor indicado por *<página_codigos>*, junto con el país o región y el idioma predeterminados (definidos por el sistema operativo host) para la página de códigos especificada.

La categoría debe ser **LC_ALL** o **LC_CTYPE** para llevar a cabo un cambio de la página de códigos. Por ejemplo, si el país o región predeterminados y el idioma del sistema operativo host son "United States" y "Inglés", las dos llamadas siguientes a **setlocale** son funcionalmente equivalentes:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Para obtener más información, vea la directiva pragma [setlocale](../../preprocessor/setlocale.md) en [Referencia del preprocesador de C/C++](../../preprocessor/c-cpp-preprocessor-reference.md).

La función [_configthreadlocale](configthreadlocale.md) se utiliza para controlar si **setlocale** afecta a la configuración regional de todos los subprocesos en un programa o solo la configuración regional del subproceso que realiza la llamada.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**setlocale**|\<locale.h>|
|**_wsetlocale**|\<locale.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

```C
// crt_setlocale.c
//
// This program demonstrates the use of setlocale when
// using two independent threads.
//

#include <locale.h>
#include <process.h>
#include <windows.h>
#include <stdio.h>
#include <time.h>

#define BUFF_SIZE 100

// Retrieve the date in the current
// locale's format.
int get_date(unsigned char* str)
{
    __time64_t ltime;
    struct tm  thetime;

    // Retrieve the current time
    _time64(&ltime);
    _gmtime64_s(&thetime, &ltime);

    // Format the current time structure into a string
    // "%#x" is the long date representation in the
    // current locale
    if (!strftime((char *)str, BUFF_SIZE, "%#x",
                  (const struct tm *)&thetime))
    {
        printf("strftime failed!\n");
        return -1;
    }
    return 0;
}

// This thread sets its locale to the argument
// and prints the date.
uintptr_t __stdcall SecondThreadFunc( void* pArguments )
{
    unsigned char str[BUFF_SIZE];
    char * locale = (char *)pArguments;

    // Set the thread locale
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, locale));

    // Retrieve the date string from the helper function
    if (get_date(str) == 0)
    {
        printf("The date in %s locale is: '%s'\n", locale, str);
    }

    _endthreadex( 0 );
    return 0;
}

// The main thread sets the locale to English
// and then spawns a second thread (above) and prints the date.
int main()
{
    HANDLE          hThread;
    unsigned        threadID;
    unsigned char   str[BUFF_SIZE];

    // Configure per-thread locale to cause all subsequently created
    // threads to have their own locale.
    _configthreadlocale(_ENABLE_PER_THREAD_LOCALE);

    // Set the locale of the main thread to US English.
    printf("The thread locale is now set to %s.\n",
           setlocale(LC_ALL, "en-US"));

    // Create the second thread with a German locale.
    // Our thread function takes an argument of the locale to use.
    hThread = (HANDLE)_beginthreadex( NULL, 0, &SecondThreadFunc,
                                      "de-DE", 0, &threadID );

    if (get_date(str) == 0)
    {
        // Retrieve the date string from the helper function
        printf("The date in en-US locale is: '%s'\n\n", str);
    }

    // Wait for the created thread to finish.
    WaitForSingleObject( hThread, INFINITE );

    // Destroy the thread object.
    CloseHandle( hThread );
}
```

```Output
The thread locale is now set to en-US.
The time in en-US locale is: 'Wednesday, May 12, 2004'

The thread locale is now set to de-DE.
The time in de-DE locale is: 'Mittwoch, 12. Mai 2004'
```

## <a name="see-also"></a>Vea también

[Nombres de configuración regional, idiomas y cadenas de país/región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)<br/>
[_configthreadlocale](configthreadlocale.md)<br/>
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)<br/>
[Configuración regional](../../c-runtime-library/locale.md)<br/>
[localeconv](localeconv.md)<br/>
[_mbclen, mblen, _mblen_l](mbclen-mblen-mblen-l.md)<br/>
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)<br/>
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)<br/>
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)<br/>
[_setmbcp](setmbcp.md)<br/>
[strcoll (funciones)](../../c-runtime-library/strcoll-functions.md)<br/>
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)<br/>
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)<br/>
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)<br/>
[wctomb, _wctomb_l](wctomb-wctomb-l.md)<br/>
