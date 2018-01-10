---
title: _CrtDbgReport, _CrtDbgReportW | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
apiname:
- _CrtDbgReport
- _CrtDbgReportW
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
- CrtDbgReport
- CrtDbgReportW
- _CrtDbgReportW
- _CrtDbgReport
dev_langs: C++
helpviewer_keywords:
- debug reporting
- _CrtDbgReport function
- CrtDbgReport function
- CrtDbgReportW function
- _CrtDbgReportW function
ms.assetid: 6e581fb6-f7fb-4716-9432-f0145d639ecc
caps.latest.revision: "18"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a2f148b031312db10449c6f33c67b94f6e171c5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="crtdbgreport-crtdbgreportw"></a>_CrtDbgReport, _CrtDbgReportW
Genera un informe con un mensaje de depuración y lo envía a tres destinos posibles (solo versión de depuración).  
  
## <a name="syntax"></a>Sintaxis  
  
```  
int _CrtDbgReport(   
   int reportType,  
   const char *filename,  
   int linenumber,  
   const char *moduleName,  
   const char *format [,  
   argument] ...   
);  
int _CrtDbgReportW(   
   int reportType,  
   const wchar_t *filename,  
   int linenumber,  
   const wchar_t *moduleName,  
   const wchar_t *format [,  
   argument] ...   
);  
```  
  
#### <a name="parameters"></a>Parámetros  
 `reportType`  
 Tipo de informe: `_CRT_WARN`, `_CRT_ERROR` y `_CRT_ASSERT`.  
  
 `filename`  
 Puntero al nombre del archivo de código fuente donde se produjo la aserción o el informe, o `NULL`.  
  
 `linenumber`  
 Número de la línea del archivo de código fuente donde se produjo la aserción o el informe, o `NULL`.  
  
 `moduleName`  
 Puntero al nombre del módulo (.exe o .dll) donde se produjo la aserción o el informe.  
  
 `format`  
 Puntero a la cadena de control de formato utilizada para crear el mensaje de usuario.  
  
 `argument`  
 Argumentos de sustitución opcionales utilizados por `format`.  
  
## <a name="return-value"></a>Valor devuelto  
 Para todos los destinos de informe, `_CrtDbgReport` y `_CrtDbgReportW` devuelven -1 si se produce un error y 0 si no se encuentran errores. En cambio, cuando el destino del informe es una ventana de mensajes de depuración y el usuario hace clic en el botón **Reintentar**, estas funciones devuelven 1. Si el usuario hace clic en el botón **Anular** de la ventana de mensajes de depuración, estas funciones se anulan inmediatamente y no devuelven ningún valor.  
  
 Las macros de depuración [_RPT, _RPTF](../../c-runtime-library/reference/rpt-rptf-rptw-rptfw-macros.md) llaman a `_CrtDbgReport` para generar los informes de depuración. Las versiones de caracteres anchos de estas macros, así como [_ASSERT&#91;E&#93;](../../c-runtime-library/reference/assert-asserte-assert-expr-macros.md), `_RPTW n` y `_RPTFW n`, usan `_CrtDbgReportW` para generar los informes de depuración. Si `_CrtDbgReport` o `_CrtDbgReportW` devuelven 1, estas macros inician el depurador, siempre que esté habilitada la depuración Just-in-time (JIT).  
  
## <a name="remarks"></a>Comentarios  
 `_CrtDbgReport` y `_CrtDbgReportW` pueden enviar el informe de depuración a tres destinos distintos: un archivo de informe de depuración, un monitor de depuración (el depurador [!INCLUDE[vsprvs](../../assembler/masm/includes/vsprvs_md.md)]) o una ventana de mensajes de depuración. Se usan dos funciones de configuración, [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) y [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md), para especificar los destinos de cada tipo de informe. Estas funciones permiten controlar por separado los destinos de los informes de cada tipo de informe. Por ejemplo, se puede especificar que un parámetro `reportType` de `_CRT_WARN` se envíe solo al monitor de depuración, y que el parámetro `reportType` de `_CRT_ASSERT` se envíe a una ventana de mensajes de depuración y a un archivo de informe definido por el usuario.  
  
 `_CrtDbgReportW` es la versión con caracteres anchos de `_CrtDbgReport`. Todos sus parámetros de salida y de cadena son cadenas de caracteres anchos; por lo demás, es idéntica a la versión de caracteres de un solo byte.  
  
 `_CrtDbgReport` y `_CrtDbgReportW` crean el mensaje de usuario para el informe de depuración sustituyendo los argumentos de `argument`[`n`] de la cadena `format`, con las mismas reglas definidas por las funciones `printf` o `wprintf`. A continuación, estas funciones generan el informe de depuración y determinan los destinos en función de los modos de informe actuales y el archivo definidos para `reportType`. Cuando el informe se envía a una ventana de mensajes de depuración, los parámetros `filename`, `lineNumber` y `moduleName` se incluyen en la información que se muestra en la ventana.  
  
 En la tabla siguiente se enumeran las opciones de los modos y el archivo de informe, y el comportamiento que producen `_CrtDbgReport` y `_CrtDbgReportW`. Estas opciones se definen como marcas de bits en \<crtdbg.h>.  
  
|Modo de informe|Archivo de informe|Comportamiento de `_CrtDbgReport` y `_CrtDbgReportW`|  
|-----------------|-----------------|------------------------------------------------|  
|`_CRTDBG_MODE_DEBUG`|No es aplicable|Escribe el mensaje mediante la API [OutputDebugString](http://msdn.microsoft.com/library/windows/desktop/aa363362.aspx) de Windows.|  
|`_CRTDBG_MODE_WNDW`|No es aplicable|Llama a la API [MessageBox](http://msdn.microsoft.com/library/windows/desktop/ms645505) de Windows para crear el cuadro de mensaje en el que se mostrará el mensaje junto con los botones **Anular**, **Reintentar** y **Omitir**. Si un usuario hace clic en **Anular`_CrtDbgReport`,**  o `_CrtDbgReport` se anulan automáticamente. Si un usuario hace clic en **Reintentar**, devuelve 1. Si un usuario hace clic en **Omitir**, la ejecución continúa y `_CrtDbgReport` y `_CrtDbgReportW` devuelven 0. Observe que si se hace clic en **Omitir** cuando existe una condición de error, se suele producir un "comportamiento indefinido".|  
|`_CRTDBG_MODE_FILE`|`__HFILE`|Escribe el mensaje en el `HANDLE` suministrado por el usuario, mediante la API [WriteFile](http://msdn.microsoft.com/library/windows/desktop/aa365747.aspx) de Windows, y no comprueba la validez del identificador de archivo. La aplicación se ocupa de abrir el archivo de informe y pasar un identificador de archivo válido.|  
|`_CRTDBG_MODE_FILE`|`_CRTDBG_FILE_STDERR`|Escribe el mensaje en `stderr`.|  
|`_CRTDBG_MODE_FILE`|`_CRTDBG_FILE_STDOUT`|Escribe el mensaje en `stdout`.|  
  
 El informe se puede enviar a uno, dos o tres destinos, o a ninguno. Para obtener más información sobre cómo especificar los modos de informe y el archivo de informe, consulte las funciones [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md) y [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md). Para obtener más información sobre el uso de las macros de depuración y las funciones de creación de informes, consulte [Macros para los informes](/visualstudio/debugger/macros-for-reporting).  
  
 Si la aplicación necesita más flexibilidad que la que `_CrtDbgReport` y `_CrtDbgReportW` ofrecen, puede escribir su propia función de creación de informes y enlazarla al mecanismo de creación de informes de la biblioteca en tiempo de ejecución de C mediante la función [_CrtSetReportHook](../../c-runtime-library/reference/crtsetreporthook.md).  
  
## <a name="requirements"></a>Requisitos  
  
|Rutina|Encabezado necesario|  
|-------------|---------------------|  
|`_CrtDbgReport`|\<crtdbg.h>|  
|`_CrtDbgReportW`|\<crtdbg.h>|  
  
 `_CrtDbgReport` y `_CrtDbgReportW` son extensiones de Microsoft. Para obtener más información, vea [Compatibilidad](../../c-runtime-library/compatibility.md).  
  
## <a name="libraries"></a>Bibliotecas  
 Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).  
  
## <a name="example"></a>Ejemplo  
  
```  
// crt_crtdbgreport.c  
#include <crtdbg.h>  
  
int main(int argc, char *argv[]) {  
#ifdef _DEBUG  
   _CrtDbgReport(_CRT_ASSERT, __FILE__, __LINE__, argv[0], NULL);  
#endif  
}  
```  
  
 Consulte [crt_dbg2](http://msdn.microsoft.com/en-us/21e1346a-6a17-4f57-b275-c76813089167) para obtener un ejemplo de cómo cambiar la función de informes.  
  
## <a name="see-also"></a>Vea también  
 [Rutinas de depuración](../../c-runtime-library/debug-routines.md)   
 [_CrtSetReportMode](../../c-runtime-library/reference/crtsetreportmode.md)   
 [_CrtSetReportFile](../../c-runtime-library/reference/crtsetreportfile.md)   
 [printf, _printf_l, wprintf, _wprintf_l](../../c-runtime-library/reference/printf-printf-l-wprintf-wprintf-l.md)   
 [_DEBUG](../../c-runtime-library/debug.md)