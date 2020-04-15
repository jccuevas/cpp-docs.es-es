---
title: _putenv, _wputenv
ms.date: 4/2/2020
api_name:
- _putenv
- _wputenv
- _o__putenv
- _o__wputenv
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
- api-ms-win-crt-private-l1-1-0
api_type:
- DLLExport
topic_type:
- apiref
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
ms.openlocfilehash: 3e74959e6c6cdb2e27ce0d68ba40d02d64949904
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81333042"
---
# <a name="_putenv-_wputenv"></a>_putenv, _wputenv

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

Devuelve 0 si se realiza correctamente o -1 en caso de error.

## <a name="remarks"></a>Observaciones

La función **_putenv** agrega nuevas variables de entorno o modifica los valores de las variables de entorno existentes. Las variables de entorno definen el entorno en el que se ejecuta un proceso (por ejemplo, la ruta de búsqueda predeterminada para vincular bibliotecas a un programa). **_wputenv** es una versión de caracteres anchos de **_putenv;** el argumento *envstring* para **_wputenv** es una cadena de caracteres anchos.

De forma predeterminada, el estado global de esta función se limita a la aplicación. Para cambiar esto, consulte [Estado global en el CRT](../global-state.md).

### <a name="generic-text-routine-mappings"></a>Asignaciones de rutina de texto genérico

|Rutina Tchar.h|_UNICODE y _MBCS no definidos|_MBCS definido|_UNICODE definido|
|---------------------|--------------------------------------|--------------------|-----------------------|
|**_tputenv**|**_putenv**|**_putenv**|**_wputenv**|

El argumento *envstring* debe ser un puntero a una cadena del formulario *varname*=*value_string*, donde *varname* es el nombre de la variable de entorno que se va a agregar o modificar y *value_string* es el valor de la variable. Si *varname* ya forma parte del entorno, su valor se sustituye por *value_string*; de lo contrario, la nueva variable *varname* y su valor *value_string* se agregan al entorno. Puede quitar una variable del entorno especificando un *value_string*vacío o, en otras palabras, especificando solo *varname*.

**_putenv** y **_wputenv** solo afectan al entorno local del proceso actual; no puede utilizarlos para modificar el entorno de nivel de comando. Dicho de otro modo, estas funciones solo funcionan en estructuras de datos a las que puede tener acceso la biblioteca en tiempo de ejecución y no en el segmento de entorno creado para un proceso por el sistema operativo. Cuando finaliza el proceso actual, el entorno vuelve al nivel del proceso de llamada (en la mayoría de los casos, el nivel del sistema operativo). Sin embargo, el entorno modificado se puede pasar a cualquier proceso nuevo creado por **_spawn,** **_exec**o **sistema,** y estos nuevos procesos obtienen los nuevos elementos agregados por **_putenv** y **_wputenv**.

No cambie una entrada de entorno directamente: en su lugar, utilice **_putenv** o **_wputenv** para cambiarla. En particular, los elementos de liberación directa de la matriz global **_environ[]** pueden dar lugar a que se dirija la memoria no válida.

**getenv** y **_putenv** utilizan la variable global **_environ** para tener acceso a la tabla de entorno; **_wgetenv** y **_wputenv** utilizar **_wenviron**. **_putenv** y **_wputenv** pueden cambiar el valor de **_environ** y **_wenviron**, invalidando así el argumento **_envp** a **main** y el argumento **_wenvp** a **wmain**. Por lo tanto, es más seguro utilizar **_environ** o **_wenviron** para acceder a la información del entorno. Para obtener más información sobre la relación de **_putenv** y **_wputenv** con variables globales, consulte [_environ, _wenviron](../../c-runtime-library/environ-wenviron.md).

> [!NOTE]
> Las **_putenv** y **_getenv** familias de funciones no son seguras para subprocesos. **_getenv** podría devolver un puntero de cadena mientras **_putenv** está modificando la cadena, lo que provoca errores aleatorios. Asegúrese de que las llamadas a estas funciones están sincronizadas.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_putenv**|\<stdlib.h>|
|**_wputenv**|\<stdlib.h> o \<wchar.h>|

Para obtener más información sobre compatibilidad, vea [Compatibility](../../c-runtime-library/compatibility.md).

## <a name="example"></a>Ejemplo

Para obtener un ejemplo de cómo utilizar **_putenv**, vea [getenv, _wgetenv](getenv-wgetenv.md).

## <a name="see-also"></a>Consulte también

[Control de Procesos y Medio Ambiente](../../c-runtime-library/process-and-environment-control.md)<br/>
[getenv, _wgetenv](getenv-wgetenv.md)<br/>
[_searchenv, _wsearchenv](searchenv-wsearchenv.md)<br/>
