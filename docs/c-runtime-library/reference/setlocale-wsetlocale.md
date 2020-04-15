---
title: setlocale, _wsetlocale
description: Describe las funciones setlocale de biblioteca en _wsetlocaletiempo de ejecución de Microsoft C (CRT) y .
ms.date: 4/2/2020
api_name:
- _wsetlocale
- setlocale
- _o__wsetlocale
- _o_setlocale
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
no-loc:
- setlocale
- _wsetlocale
ms.openlocfilehash: 2834229839153c3154caadf71e5fb30d84ed2f1a
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81353722"
---
# <a name="setlocale-_wsetlocale"></a>setlocale, _wsetlocale

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

*Categoría*\
Categoría afectada por la configuración regional.

*Configuración regional*\
Especificador de la configuración regional.

## <a name="return-value"></a>Valor devuelto

Si se proporciona una *configuración regional* y una *categoría* válidas, devuelve un puntero a la cadena asociada a la configuración *regional* y la *categoría*especificadas. Si la *configuración regional* o la *categoría* no es válida, devuelve un puntero nulo y la configuración regional actual del programa no cambia.

Por ejemplo, la llamada

```C
setlocale( LC_ALL, "en-US" );
```

establece todas las categorías y devuelve solo la cadena

```Output
en-US
```

Puede copiar la cadena devuelta por **setlocale** para restaurar esa parte de la información de configuración regional del programa. El almacenamiento local global o de subprocesos se utiliza para la cadena devuelta por **setlocale**. Las llamadas posteriores a **setlocale** sobrescriben la cadena, lo que invalida los punteros de cadena devueltos por llamadas anteriores.

## <a name="remarks"></a>Observaciones

Utilice la función **setlocale** para establecer, cambiar o consultar parte o toda la información de configuración regional del programa actual especificada por *la configuración regional* y la *categoría*. *la* configuración regional se refiere a la localidad (país/región e idioma) para la que puede personalizar ciertos aspectos de su programa. Entre las categorías dependientes de la configuración regional se encuentran el formato de fechas y el formato de presentación de valores de moneda. Si establece la configuración *regional* en la cadena predeterminada para un idioma que tiene varios formularios admitidos en el equipo, debe comprobar el valor devuelto **setlocale** para ver qué idioma está en vigor. Por ejemplo, si establece *la configuración regional* en "chino", el valor devuelto podría ser "chino simplificado" o "chino-tradicional".

**_wsetlocale** es una versión de caracteres anchos de **setlocale;** el argumento *de configuración* regional y el valor devuelto de **_wsetlocale** son cadenas de caracteres anchos. **_wsetlocale** y **setlocale** se comportan de forma idéntica de lo contrario.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tsetlocale**|**setlocale**|**setlocale**|**_wsetlocale**|

El argumento *category* especifica las partes de la información de configuración regional de un programa que se ven afectadas. Las macros utilizadas para la *categoría* y las partes del programa que afectan son las siguientes:

|bandera *de categoría*|Afecta a|
|-|-|
| **LC_ALL** | Todas las categorías, como se indica a continuación. |
| **LC_COLLATE** | Las **funciones strcoll**, **_stricoll**, **wcscoll**, **_wcsicoll**, **strxfrm**, **_strncoll**, **_strnicoll**, **_wcsncoll**, **_wcsnicoll**y **wcsxfrm.** |
| **LC_CTYPE** | Las funciones de control de caracteres (excepto **isdigit**, **isxdigit**, **mbstowcs**y **mbtowc**, que no se ven afectadas). |
| **LC_MONETARY** | Información de formato monetario devuelta por la función **localeconv.** |
| **LC_NUMERIC** | Carácter de punto decimal para las rutinas de salida con formato (como **printf**), para las rutinas de conversión de datos y para la información de formato no monetario devuelta por **localeconv**. Además del carácter decimal, **LC_NUMERIC** establece el separador de miles y la cadena de control de agrupación devuelta por [localeconv](localeconv.md). |
| **LC_TIME** | Las funciones **strftime** y **wcsftime.** |

Esta función valida el parámetro de categoría. Si el parámetro category no es uno de los valores especificados en la tabla anterior, se invoca el controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, la función establece **errno en** **EINVAL** y devuelve **NULL**.

El argumento *de configuración* regional es un puntero a una cadena que especifica la configuración regional. Para obtener información sobre el formato del argumento *de configuración regional,* vea Nombres de [configuración regional, idiomas y cadenas](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)de país o región . Si *locale* señala a una cadena vacía, la configuración regional es el entorno nativo definido por la implementación. Un valor de **C** especifica el entorno de conformidad ANSI mínimo para la traducción de C. La configuración regional de **C** supone que todos los tipos de datos **char** son de 1 byte y que su valor siempre es inferior a 256.

Durante el inicio del programa, se ejecuta el equivalente de la instrucción siguiente:

`setlocale( LC_ALL, "C" );`

El argumento *de configuración* regional puede tomar un nombre de configuración regional, una cadena de idioma, una cadena de idioma y un código de país o región, una página de códigos o una cadena de idioma, un código de país o región y una página de códigos. El conjunto de nombres de configuración regional, idiomas, códigos de país o región y páginas de códigos disponibles incluye todos los admitidos por la API de Windows NLS. El conjunto de nombres de configuración regional admitidos por **setlocale** se describe en Nombres de [configuración regional, idiomas y cadenas](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)de país o región . El conjunto de cadenas de idioma y país/región admitidos por **setlocale** se enumeran en Cadenas de [idioma](../../c-runtime-library/language-strings.md) y Cadenas de [país/región](../../c-runtime-library/country-region-strings.md). Se recomienda emplear el formato del nombre de la configuración regional para mejorar el rendimiento y simplificar el mantenimiento de las cadenas de configuración regional insertadas en código o serializadas en el almacenamiento. Es menos probable que una actualización del sistema operativo cambie las cadenas de nombre de configuración regional que el formato de nombre de idioma y de país o región.

Un puntero nulo que se pasa como argumento *de configuración* regional indica a **setlocale** que consulte en lugar de establecer el entorno internacional. Si el argumento *de configuración* regional es un puntero nulo, no se cambia la configuración regional actual del programa. En su lugar, **setlocale** devuelve un puntero a la cadena asociada a la *categoría* de la configuración regional actual del subproceso. Si el argumento *category* es **LC_ALL**, la función devuelve una cadena que indica la configuración actual de cada categoría, separada por punto y coma. Por ejemplo, la secuencia de llamadas

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

que es la cadena que está asociada con la categoría **LC_ALL.**

Los siguientes ejemplos pertenecen a la categoría **LC_ALL.** Cualquiera de las cadenas ". OCP" y ". ACP" se puede utilizar en lugar de un número de página de códigos para especificar el uso de la página de códigos OEM predeterminada del usuario y la página de códigos ANSI predeterminada por el usuario para ese nombre de configuración regional, respectivamente.

- `setlocale( LC_ALL, "" );`

   Establece la configuración regional en el valor predeterminado, que es la página de códigos ANSI predeterminada del usuario obtenida del sistema operativo. El nombre de configuración regional se establece en el valor devuelto por [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). La página de códigos se establece en el valor devuelto por [GetACP](/windows/win32/api/winnls/nf-winnls-getacp).

- `setlocale( LC_ALL, ".OCP" );`

   Establece la configuración regional en la página de códigos OEM actual obtenida del sistema operativo. El nombre de configuración regional se establece en el valor devuelto por [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). La página de códigos se establece en el valor [de LOCALE_IDEFAULTCODEPAGE](/windows/win32/intl/locale-idefault-constants) para el nombre de configuración regional predeterminado del usuario mediante [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, ".ACP" );`

   Establece la configuración regional en la página de códigos ANSI obtenida del sistema operativo. El nombre de configuración regional se establece en el valor devuelto por [GetUserDefaultLocaleName](/windows/win32/api/winnls/nf-winnls-getuserdefaultlocalename). La página de códigos se establece en el valor [de LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) para el nombre de configuración regional predeterminado del usuario mediante [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<localename>" );`

   Establece la configuración regional en el nombre de * \< *configuración regional que se indica mediante el nombre de configuración regional>. La página de códigos se establece en el valor [de LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) para el nombre de configuración regional especificado por [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>" );`

   Establece la configuración regional en el idioma * \<* y el país o región indicados por el idioma>y * \<el país>, *junto con la página de códigos predeterminada obtenida del sistema operativo host. La página de códigos se establece en el valor [de LOCALE_IDEFAULTANSICODEPAGE](/windows/win32/intl/locale-idefault-constants) para el nombre de configuración regional especificado por [GetLocaleInfoEx](/windows/win32/api/winnls/nf-winnls-getlocaleinfoex).

- `setlocale( LC_ALL, "<language>_<country>.<code_page>" );`

   Establece la configuración regional en el idioma, el país o la * \< *región y la página de códigos indicados por las * \< *cadenas de>de idioma,>de país y * \<code_page>.* Puede utilizar distintas combinaciones de idioma, país o región y página de códigos. Por ejemplo, esta llamada establece la configuración regional en francés de Canadá con la página de códigos 1252:

   `setlocale( LC_ALL, "French_Canada.1252" );`

   Esta llamada establece la configuración regional en francés de Canadá con la página de códigos ANSI predeterminada:

   `setlocale( LC_ALL, "French_Canada.ACP" );`

   Esta llamada establece la configuración regional en francés de Canadá con la página de códigos OEM predeterminada:

   `setlocale( LC_ALL, "French_Canada.OCP" );`

- `setlocale( LC_ALL, "<language>" );`

   Establece la configuración regional en el idioma * \< *indicado por>de idioma y utiliza el país o región predeterminado para el idioma especificado y la página de códigos ANSI predeterminada del usuario para ese país o región obtenida del sistema operativo host. Por ejemplo, las siguientes llamadas a **setlocale** son funcionalmente equivalentes:

   `setlocale( LC_ALL, "en-US" );`

   `setlocale( LC_ALL, "English" );`

   `setlocale( LC_ALL, "English_United States.1252" );`

   Se recomienda usar el primer formato para mejorar el rendimiento y el mantenimiento.

- `setlocale( LC_ALL, ".<code_page>" );`

   Establece la página de códigos en el valor indicado por *<página_codigos>*, junto con el país o región y el idioma predeterminados (definidos por el sistema operativo host) para la página de códigos especificada.

La categoría debe ser **LC_ALL** o **LC_CTYPE** para realizar un cambio de página de códigos. Por ejemplo, si el país o región predeterminado y el idioma del sistema operativo host son "Estados Unidos" e "Inglés", las dos llamadas siguientes a **setlocale** son funcionalmente equivalentes:

`setlocale( LC_ALL, ".1252" );`

`setlocale( LC_ALL, "English_United States.1252");`

Para obtener más información, vea la directiva pragma [setlocale](../../preprocessor/setlocale.md) en [Referencia del preprocesador de C/C++](../../preprocessor/c-cpp-preprocessor-reference.md).

La función [_configthreadlocale](configthreadlocale.md) se utiliza para controlar si **setlocale** afecta a la configuración regional de todos los subprocesos de un programa o solo a la configuración regional del subproceso que realiza la llamada.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**setlocale**|\<locale.h>|
|**_wsetlocale**|\<locale.h> o \<wchar.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

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

    // Enable per-thread locale causes all subsequent locale
    // setting changes in this thread to only affect this thread.
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

## <a name="see-also"></a>Consulte también

[Nombres de configuración regional, idiomas y cadenas de país/región](../../c-runtime-library/locale-names-languages-and-country-region-strings.md)\
[_configthreadlocale](configthreadlocale.md)\
[_create_locale, _wcreate_locale](create-locale-wcreate-locale.md)\
[Configuración regional](../../c-runtime-library/locale.md)\
[localeconv](localeconv.md)\
[_mbclen, Mblen, _mblen_l](mbclen-mblen-mblen-l.md)\
[strlen, wcslen, _mbslen, _mbslen_l, _mbstrlen, _mbstrlen_l](strlen-wcslen-mbslen-mbslen-l-mbstrlen-mbstrlen-l.md)\
[mbstowcs, _mbstowcs_l](mbstowcs-mbstowcs-l.md)\
[mbtowc, _mbtowc_l](mbtowc-mbtowc-l.md)\
[_setmbcp](setmbcp.md)\
[Funciones strcoll](../../c-runtime-library/strcoll-functions.md)\
[strftime, wcsftime, _strftime_l, _wcsftime_l](strftime-wcsftime-strftime-l-wcsftime-l.md)\
[strxfrm, wcsxfrm, _strxfrm_l, _wcsxfrm_l](strxfrm-wcsxfrm-strxfrm-l-wcsxfrm-l.md)\
[wcstombs, _wcstombs_l](wcstombs-wcstombs-l.md)\
[wctomb, _wctomb_l](wctomb-wctomb-l.md)
