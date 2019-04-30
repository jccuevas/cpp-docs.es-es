---
title: _CrtSetReportFile
ms.date: 11/04/2016
apiname:
- _CrtSetReportFile
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
apitype: DLLExport
f1_keywords:
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: 32a560e09c47468daf48c185e23d6e289c6d1d9b
ms.sourcegitcommit: c6f8e6c2daec40ff4effd8ca99a7014a3b41ef33
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/24/2019
ms.locfileid: "64343017"
---
# <a name="crtsetreportfile"></a>_CrtSetReportFile

Después de usar [_CrtSetReportMode](crtsetreportmode.md) especificar **_CRTDBG_MODE_FILE**, puede especificar el identificador de archivo para recibir el texto del mensaje. **_CrtSetReportFile** también usa [_CrtDbgReport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) para especificar el destino de texto (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>Parámetros

*reportType*<br/>
Tipo de informe: **_CRT_WARN**, **_CRT_ERROR**, y **_CRT_ASSERT**.

*reportFile*<br/>
Nuevo archivo de informe para *reportType*.

## <a name="return-value"></a>Valor devuelto

Se completa correctamente, **_CrtSetReportFile** devuelve el archivo de informe anterior definido para el tipo de informe especificado en *reportType*. Si se pasa un valor no válido para *reportType*, esta función invoca al controlador de parámetros no válidos, como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** está establecido en **EINVAL** y la función devuelve **_CRTDBG_HFILE_ERROR**. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

**_CrtSetReportFile** se usa con el [_CrtSetReportMode](crtsetreportmode.md) función para definir el destino o destinos de un tipo de informe específico generado por **_CrtDbgReport**. Cuando **_CrtSetReportMode** se ha llamado para asignar el **_CRTDBG_MODE_FILE** modo para un tipo específico de informe, reporting **_CrtSetReportFile** , a continuación, se debe llamar a Defina el archivo o flujo concreto que se usará como el destino. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtSetReportFile** se quitan durante el preprocesamiento.

La siguiente lista muestra las opciones disponibles para *reportFile* y el comportamiento resultante de **_CrtDbgReport**. Estas opciones se definen como marcas de bits en Crtdbg.h.

- **identificador de archivo**

   Identificador del archivo que será el destino de los mensajes. No se intenta comprobar la validez del identificador. Es necesario abrir y cerrar el identificador del archivo. Por ejemplo:

   ```C
   HANDLE hLogFile;
   hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,
      FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,
      FILE_ATTRIBUTE_NORMAL, NULL);
   _CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_WARN, hLogFile);

   _RPT0(_CRT_WARN,"file message\n");
   CloseHandle(hLogFile);
   ```

- **_CRTDBG_FILE_STDERR**

   Escribe el mensaje en **stderr**, que se pueden redirigir como sigue:

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   Escribe el mensaje en **stdout**, que se pueden redirigir.

- **_CRTDBG_REPORT_FILE**

   Devuelve el modo de creación de informes actual.

El archivo de informe utilizado por cada tipo de informe se puede controlar por separado. Por ejemplo, es posible especificar que un *reportType* de **_CRT_ERROR** notificará a **stderr**, mientras que un *reportType* de **_CRT_ASSERT** notificará a un identificador de archivo definido por el usuario o una secuencia.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

La consola no se admite en aplicaciones de la plataforma Universal de Windows (UWP). Los identificadores de secuencia estándar que están asociados con la consola, **stdin**, **stdout**, y **stderr**, se deben redirigir antes las funciones de tiempo de ejecución de C puedan usarlos en aplicaciones para UWP . Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Bibliotecas:** Versiones de depuración de [características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md) solo.

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
