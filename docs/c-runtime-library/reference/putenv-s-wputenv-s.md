---
title: _putenv_s, _wputenv_s
ms.date: 11/04/2016
api_name:
- _wputenv_s
- _putenv_s
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
- api-ms-win-crt-environment-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- putenv_s
- wputenv_s
- _wputenv_s
- _putenv_s
helpviewer_keywords:
- wputenv_s function
- _putenv_s function
- environment variables, deleting
- putenv_s function
- _wputenv_s function
- environment variables, creating
- environment variables, modifying
ms.assetid: fbf51225-a8da-4b9b-9d7c-0b84ef72df18
ms.openlocfilehash: b2de609314a12f626a21680b470bc8831eada2cb
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70949902"
---
# <a name="_putenv_s-_wputenv_s"></a>_putenv_s, _wputenv_s

Crea, modifica o quita variables de entorno. Se trata de versiones de [_putenv, _wputenv](putenv-wputenv.md) que tienen mejoras de seguridad, tal y como se describe en [Características de seguridad de CRT](../../c-runtime-library/security-features-in-the-crt.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
errno_t _putenv_s(
   const char *varname,
   const char *value_string
);
errno_t _wputenv_s(
   const wchar_t *varname,
   const wchar_t *value_string
);
```

### <a name="parameters"></a>Parámetros

*varname*<br/>
Nombre de la variable de entorno.

*value_string*<br/>
Valor en el que se establece la variable de entorno.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si se ejecuta correctamente; de lo contrario, devuelve un código de error.

### <a name="error-conditions"></a>Condiciones de error

|*varname*|*value_string*|Valor devuelto|
|------------|-------------|------------------|
|**NULL**|any|**EINVAL**|
|any|**NULL**|**EINVAL**|

Si se produce una de las condiciones de error, estas funciones invocan el controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, estas funciones devuelven **EINVAL** y establecen **errno** en **EINVAL**.

## <a name="remarks"></a>Comentarios

La función **_putenv_s** agrega nuevas variables de entorno o modifica los valores de las variables de entorno existentes. Las variables de entorno definen el entorno en el que se ejecuta un proceso (por ejemplo, la ruta de búsqueda predeterminada para vincular bibliotecas a un programa). **_wputenv_s** es una versión con caracteres anchos de **_putenv_s**; el argumento *envstring* para **_wputenv_s** es una cadena de caracteres anchos.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina TCHAR.H|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|------------------------------------|--------------------|-----------------------|
|**_tputenv_s**|**_putenv_s**|**_putenv_s**|**_wputenv_s**|

*varname* es el nombre de la variable de entorno que se va a agregar o modificar y *value_string* es el valor de la variable. Si *varname* ya forma parte del entorno, su valor se reemplaza por *value_string*; de lo contrario, la nueva variable *varname* y su *value_string* se agregan al entorno. Puede quitar una variable del entorno especificando una cadena vacía (es decir, "") para *value_string*.

**_putenv_s** y **_wputenv_s** solo afectan al entorno que es local en el proceso actual; no se pueden usar para modificar el entorno de nivel de comandos. Solo funcionan en estructuras de datos a las que puede tener acceso la biblioteca en tiempo de ejecución y no en el "segmento" de entorno que el sistema operativo crea para un proceso. Cuando finaliza el proceso actual, el entorno vuelve al nivel del proceso de llamada, que en la mayoría de los casos es el nivel del sistema operativo. Sin embargo, el entorno modificado se puede pasar a cualquier proceso nuevo creado por **_spawn**, **_exec**o **System**, y estos nuevos procesos obtienen los nuevos elementos que se agregan mediante **_putenv_s** y **_wputenv_s**.

No cambie directamente una entrada de entorno; en su lugar, use **_putenv_s** o **_wputenv_s** para cambiarlo. En concreto, la liberación directa de elementos de la matriz global **_environ []** podría provocar la dirección de la memoria no válida.

**getenv** y **_putenv_s** usan la variable global **_environ** para tener acceso a la tabla de entorno. **_wgetenv** y **_wputenv_s** usan **_wenviron**. **_putenv_s** y **_wputenv_s** pueden cambiar el valor de **_environ** y **_wenviron**y, por tanto, invalidar el argumento *envp* en **Main** y el argumento **_wenvp** en **wmain**. Por lo tanto, es más seguro usar **_environ** o **_wenviron** para tener acceso a la información del entorno. Para obtener más información sobre la relación de **_putenv_s** y **_wputenv_s** con las variables globales, vea [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Las familias de funciones **_putenv_s** y **_getenv_s** no son seguras para subprocesos. **_getenv_s** podría devolver un puntero de cadena mientras **_putenv_s** está modificando la cadena y, por tanto, produce errores aleatorios. Asegúrese de que las llamadas a estas funciones están sincronizadas.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_putenv_s**|\<stdlib.h>|
|**_wputenv_s**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo que muestra cómo usar **_putenv_s**, consulte [getenv_s, _wgetenv_s](getenv-s-wgetenv-s.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
