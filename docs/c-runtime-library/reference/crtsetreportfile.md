---
title: _CrtSetReportFile | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
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
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportFile function
- _CrtSetReportFile function
ms.assetid: 3126537e-511b-44af-9c1c-0605265eabc4
caps.latest.revision: 16
author: corob-msft
ms.author: corob
manager: ghogen
translation.priority.ht:
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- ru-ru
- zh-cn
- zh-tw
translation.priority.mt:
- cs-cz
- pl-pl
- pt-br
- tr-tr
ms.translationtype: Machine Translation
ms.sourcegitcommit: e257f037a05c45f5b98e64ea55bd125af443b0be
ms.openlocfilehash: 339da058334fa394aa10f2eb33707203f4f1be7b
ms.contentlocale: es-es
ms.lasthandoff: 03/29/2017

---
# <a name="crtsetreportfile"></a>_CrtSetReportFile
Después de usar [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) para especificar `_CRTDBG_MODE_FILE`, puede especificar el identificador de archivos que va a recibir el texto del mensaje. `_CrtSetReportFile` también se usa con [_CrtDbgReport, _CrtDbgReportW](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) para especificar el destino del texto (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
_HFILE _CrtSetReportFile(   
   int reportType,  
   _HFILE reportFile   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `reportType`  
 Tipo de informe: `_CRT_WARN`, `_CRT_ERROR` y `_CRT_ASSERT`.  
  
 `reportFile`  
 Nuevo archivo de informe para `reportType`.  
  
## <a name="return-value"></a>Valor devuelto  
 Cuando la operación finaliza correctamente, `_CrtSetReportFile` devuelve el archivo de informe anterior definido para el tipo de informe especificado en `reportType`. Si se pasa un valor no válido a `reportType`, esta función invoca al controlador de parámetros no válidos, tal y como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si la ejecución puede continuar, `errno` se establece en `EINVAL` y la función devuelve `_CRTDBG_HFILE_ERROR`. Para obtener más información, consulte [errno, _doserrno, _sys_errlist y _sys_nerr](../../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md).  
  
## <a name="remarks"></a>Comentarios  
 `_CrtSetReportFile` se usa con la función [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) para definir los destinos de un tipo de informe específico generado por `_CrtDbgReport`. Cuando se ha llamado a `_CrtSetReportMode` para asignar el modo de creación de informes `_CRTDBG_MODE_FILE` a un tipo específico de informe, se debe llamar a `_CrtSetReportFile` para definir el archivo o flujo concreto que se va a usar como destino. Cuando no se define [_DEBUG](../../c-runtime-library/debug.md), las llamadas a `_CrtSetReportFile` se quitan durante el preprocesamiento.  
  
 En la tabla siguiente se enumeran las opciones disponibles para `reportFile` y el comportamiento resultante de `_CrtDbgReport`. Estas opciones se definen como marcas de bits en Crtdbg.h.  
  
 `file handle`  
 Identificador del archivo que será el destino de los mensajes. No se intenta comprobar la validez del identificador. Es necesario abrir y cerrar el identificador del archivo. Por ejemplo:  
  
```  
HANDLE hLogFile;  
hLogFile = CreateFile("c:\\log.txt", GENERIC_WRITE,   
   FILE_SHARE_WRITE, NULL, CREATE_ALWAYS,   
   FILE_ATTRIBUTE_NORMAL, NULL);  
_CrtSetReportMode(_CRT_WARN, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_WARN, hLogFile);  
  
_RPT0(_CRT_WARN,"file message\n");  
CloseHandle(hLogFile);  
```  
  
 `_CRTDBG_FILE_STDERR`  
 Escribe el mensaje en `stderr`, que se pueden redirigir como se indica a continuación:  
  
```  
freopen( "c:\\log2.txt", "w", stderr);  
_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_FILE);  
_CrtSetReportFile(_CRT_ERROR, _CRTDBG_FILE_STDERR);  
  
_RPT0(_CRT_ERROR,"1st message\n");  
```  
  
 `_CRTDBG_FILE_STDOUT`  
 Escribe el mensaje en `stdout`, que puede redirigir.  
  
 `_CRTDBG_REPORT_FILE`  
 Devuelve el modo de creación de informes actual.  
  
 El archivo de informe utilizado por cada tipo de informe se puede controlar por separado. Por ejemplo, se puede especificar que el destino del parámetro `reportType` de `_CRT_ERROR` sea `stderr`, mientras que el destino del parámetro `reportType` de `_CRT_ASSERT` sea un identificador de archivo o un flujo definido por el usuario.  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|Encabezado opcional|  
|-------------|---------------------|---------------------|  
|`_CrtSetReportFile`|\<crtdbg.h>|\<errno.h>|  
  
 La consola no se admite en las aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Se deben redirigir los identificadores estándar de flujo que están asociados a la consola, `stdin`, `stdout` y `stderr`, antes de que las funciones en tiempo de ejecución de C puedan usarlos en aplicaciones de [!INCLUDE[win8_appname_long](../../build/includes/win8_appname_long_md.md)]. Para obtener más información sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
 **Bibliotecas:** solo versiones de depuración de [Características de la biblioteca CRT](../../c-runtime-library/crt-library-features.md).  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)
