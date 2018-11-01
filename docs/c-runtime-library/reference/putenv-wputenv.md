---
title: _putenv, _wputenv
ms.date: 11/04/2016
apiname:
- _putenv
- _wputenv
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
- api-ms-win-crt-environment-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- _tputenv
- _wputenv
- _putenv
- wputenv
- tputenv
helpviewer_keywords:
- _putenv function
- environment variables, deleting
- putenv function
- tputenv function
- environment variables, creating
- wputenv function
- _wputenv function
- _tputenv function
- environment variables, modifying
ms.assetid: 9ba9b7fd-276e-45df-8420-d70c4204b8bd
ms.openlocfilehash: 952a4d62f6ceb6b689091ac09f6ca338d0b10864
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432518"
---
# <a name="putenv-wputenv"></a>_putenv, _wputenv

Crea, modifica o quita variables de entorno. Hay disponibles versiones más seguras de estas funciones; vea [_putenv_s, _wputenv_s](putenv-s-wputenv-s.md).

> [!IMPORTANT]
> Esta API no se puede usar en aplicaciones que se ejecutan en Windows en tiempo de ejecución. Para obtener más información, vea [Funciones de CRT no admitidas en aplicaciones de la Plataforma universal de Windows](../../cppcx/crt-functions-not-supported-in-universal-windows-platform-apps.md).

## <a name="syntax"></a>Sintaxis

```C
int _putenv(
   const char *envstring
);
int _wputenv(
   const wchar_t *envstring
);
```

### <a name="parameters"></a>Parámetros

*envstring*<br/>
Definición de cadena de entorno.

## <a name="return-value"></a>Valor devuelto

Devuelve 0 si se realiza correctamente o -1 si se produce un error.

## <a name="remarks"></a>Comentarios

El **_putenv** función agrega nuevas variables de entorno o modifica los valores de variables de entorno existente. Las variables de entorno definen el entorno en el que se ejecuta un proceso (por ejemplo, la ruta de búsqueda predeterminada para vincular bibliotecas a un programa). **_wputenv** es una versión con caracteres anchos de **_putenv**; el *envstring* argumento **_wputenv** es una cadena de caracteres anchos.

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

El *envstring* argumento debe ser un puntero a una cadena del formulario *varname*=*value_string*, donde *varname* es el nombre de variable de entorno se agregan o modifican y *value_string* es el valor de la variable. Si *varname* ya forma parte del entorno, su valor se sustituye por *value_string*; en caso contrario, el nuevo *varname* variable y su *value_string*  valor se agregan al entorno. Puede quitar una variable del entorno especificando un valor vacío *value_string*, o en otras palabras, especificando solo *varname*=.

**_putenv** y **_wputenv** solo afectan al entorno local en el proceso actual; no se pueden utilizar para modificar el entorno de nivel de comando. Dicho de otro modo, estas funciones solo funcionan en estructuras de datos a las que puede tener acceso la biblioteca en tiempo de ejecución y no en el segmento de entorno creado para un proceso por el sistema operativo. Cuando finaliza el proceso actual, el entorno vuelve al nivel del proceso de llamada (en la mayoría de los casos, el nivel del sistema operativo). Sin embargo, el entorno modificado se puede pasar a los nuevos procesos creados por **_spawn**, **_exec**, o **sistema**, y estos nuevos procesos obtienen los nuevos elementos agregados por **_putenv** y **_wputenv**.

No cambie directamente una entrada de entorno: en su lugar, use **_putenv** o **_wputenv** para cambiarlo. En concreto, liberando directamente elementos de la **[] _environ** matriz global puede dar lugar a que se redirige de memoria no válida.

**getenv** y **_putenv** usan la variable global **_environ** para tener acceso a la tabla de entorno. **_wgetenv** y **_wputenv** usar **_wenviron**. **_putenv** y **_wputenv** podría cambiar el valor de **_environ** y **_wenviron**, e invalidar así el **_envp** argumento de **principal** y **_wenvp** argumento **wmain**. Por lo tanto, resulta más seguro usar **_environ** o **_wenviron** para tener acceso a la información del entorno. Para obtener más información sobre la relación de **_putenv** y **_wputenv** a variables globales, consulte [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> El **_putenv** y **_getenv** familias de funciones no son seguros para subprocesos. **_getenv** podría devolver un puntero de cadena mientras **_putenv** modifica la cadena, lo que provoca errores aleatorios. Asegúrese de que las llamadas a estas funciones están sincronizadas.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo usar **_putenv**, consulte [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
