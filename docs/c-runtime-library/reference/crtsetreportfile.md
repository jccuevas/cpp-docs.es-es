---
title: _CrtSetReportFile
ms.date: 11/04/2016
api_name:
- _CrtSetReportFile
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
- CrtSetReportFile
- _CrtSetReportFile
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
ms.openlocfilehash: bf88bae40031f6e92d6f936ac8a50f85d6c4e36c
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70942277"
---
# <a name="_crtsetreportfile"></a>_CrtSetReportFile

Después de usar _ [crtsetreportmode](crtsetreportmode.md) para especificar **_CRTDBG_MODE_FILE**, puede especificar el identificador de archivo para recibir el texto del mensaje. _ [Crtdbgreport, _CrtDbgReportW](crtdbgreport-crtdbgreportw.md) también usa **_CrtSetReportFile** para especificar el destino del texto (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
_HFILE _CrtSetReportFile(
   int reportType,
   _HFILE reportFile
);
```

### <a name="parameters"></a>Parámetros

*reportType*<br/>
Tipo de informe: **_CRT_WARN**, **_CRT_ERROR**y **_CRT_ASSERT**.

*reportFile*<br/>
Nuevo archivo de informe para *reportType*.

## <a name="return-value"></a>Valor devuelto

Si se completa correctamente, **_CrtSetReportFile** devuelve el archivo de informe anterior definido para el tipo de informe especificado en *reportType*. Si se pasa un valor no válido para *reportType*, esta función invoca el controlador de parámetros no válidos, tal y como se describe en [validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, **errno** se establece en **EINVAL** y la función devuelve **_CRTDBG_HFILE_ERROR**. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).

## <a name="remarks"></a>Comentarios

**_CrtSetReportFile** se usa con la función _ [crtsetreportmode](crtsetreportmode.md) para definir el destino o los destinos de un tipo de informe específico generado por _ **crtdbgreport**. Cuando se ha llamado a _ **crtsetreportmode** para asignar el modo de informes **_CRTDBG_MODE_FILE** para un tipo de informe específico, se debe llamar a **_CrtSetReportFile** para definir el archivo o secuencia específico que se va a usar como destino. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtSetReportFile** se quitan durante el preprocesamiento.

La lista siguiente muestra las opciones disponibles para *reportFile* y el comportamiento resultante de _ **crtdbgreport**. Estas opciones se definen como marcas de bits en Crtdbg.h.

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

   Escribe el mensaje en **stderr**, que se puede redirigir como se indica a continuación:

   ```C
   freopen( "c:\\log2.txt", "w", stderr);
   _CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);
   _CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);

   _RPT0(_CRT_ERROR,"1st message\n");
   ```

- **_CRTDBG_FILE_STDOUT**

   Escribe el mensaje en **stdout**, que puede redirigir.

- **_CRTDBG_REPORT_FILE**

   Devuelve el modo de creación de informes actual.

El archivo de informe utilizado por cada tipo de informe se puede controlar por separado. Por ejemplo, es posible especificar que un *reportType* de **_CRT_ERROR** se notifique a **stderr**, mientras que un *reportType* de **_CRT_ASSERT** se debe informar a un identificador de archivo o un flujo definido por el usuario.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|Encabezado opcional|
|-------------|---------------------|---------------------|
|**_CrtSetReportFile**|\<crtdbg.h>|\<errno.h>|

La consola no se admite en aplicaciones de Plataforma universal de Windows (UWP). Los identificadores de flujo estándar que están asociados a la consola, **stdin**, **stdout**y **stderr**deben redirigirse antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones para UWP. Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

**Libre** Solo versiones de depuración de características de la [biblioteca CRT](../../c-runtime-library/crt-library-features.md) .

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
