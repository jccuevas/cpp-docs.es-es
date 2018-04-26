---
title: _RPT, _RPTF, _RPTW, _RPTFW (Macros) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: ''
ms.topic: reference
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
- RPT3
- RPTF4
- _RPT4
- RPT1
- _RPTF0
- RPTF3
- _RPTF4
- RPTF1
- RPT4
- _RPT1
- _RPT0
- RPT0
- _RPTF2
- RPTF0
- _RPT3
- _RPT2
- _RPTF3
- RPT2
- _RPTF1
dev_langs:
- C++
helpviewer_keywords:
- debugging [CRT], using macros
- _RPTW3 macro
- _RPT0 macro
- RPTW4 macro
- _RPTF3 macro
- _RPTW4 macro
- RPTF4 macro
- RPTFW2 macro
- RPTW macros
- RPT1 macro
- _RPTF macros
- RPTFW3 macro
- _RPTW0 macro
- _RPTF0 macro
- macros, debugging with
- _RPTW2 macro
- RPTF3 macro
- RPT3 macro
- RPT0 macro
- _RPT macros
- RPTW3 macro
- _RPTFW macros
- debug reporting macros
- RPTF macros
- RPT macros
- _RPTW macros
- RPTF2 macro
- _RPTF1 macro
- _RPT1 macro
- _RPT4 macro
- _RPTFW2 macro
- _RPTFW1 macro
- RPTF0 macro
- _RPT2 macro
- RPTFW macros
- _RPTW1 macro
- _RPTFW0 macro
- RPT4 macro
- _RPT3 macro
- _RPTFW3 macro
- _RPTF4 macro
- _RPTFW4 macro
- _RPTF2 macro
- RPTW0 macro
- RPTFW4 macro
- RPTFW0 macro
- RPTW2 macro
- RPTF1 macro
- RPT2 macro
- RPTFW1 macro
- RPTW1 macro
ms.assetid: a5bf8b30-57f7-4971-8030-e773b7a1ae13
caps.latest.revision: 14
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1692789ff2dac85e6ca33aa6b05ced6a01f30cba
ms.sourcegitcommit: ef859ddf5afea903711e36bfd89a72389a12a8d6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/20/2018
---
# <a name="rpt-rptf-rptw-rptfw-macros"></a>_RPT, _RPTF, _RPTW, _RPTFW (Macros)

Realiza el seguimiento del progreso de la aplicación generando un informe de depuración (únicamente una versión de depuración). Tenga en cuenta que *n* especifica el número de argumentos en *args* y puede ser 0, 1, 2, 3, 4 o 5.

## <a name="syntax"></a>Sintaxis

```C
_RPT
      n
      (
   reportType,
   format,
...[args]
);
_RPTFn(
   reportType,
   format,
   [args]
);
_RPTWn(
   reportType,
   format
   [args]
);
_RPTFWn(
   reportType,
   format
   [args]
);
```

### <a name="parameters"></a>Parámetros

*reportType* tipo de informe: **_CRT_WARN**, **_CRT_ERROR**, o **_CRT_ASSERT**.

*formato* cadena de control de formato utilizada para crear el mensaje de usuario.

*args* argumentos de sustitución que se usan por *formato*.

## <a name="remarks"></a>Comentarios

Todas estas macros toman el *reportType* y *formato* parámetros. Además, también pueden tomar hasta cuatro argumentos adicionales, indicados con el número anexado al nombre de la macro. Por ejemplo, **_RPT0** y **_RPTF0** no toman ningún argumento adicional, **_RPT1** y **_RPTF1** tomar *arg1*, **_RPT2** y **_RPTF2** tomar *arg1* y **arg2**, y así sucesivamente.

El **_RPT** y **_RPTF** macros son similares a los [printf](printf-printf-l-wprintf-wprintf-l.md) funciona, ya que pueden usarse para realizar un seguimiento del progreso de una aplicación durante el proceso de depuración. Sin embargo, estas macros son más flexibles que **printf** porque no deben incluirse en **#ifdef** instrucciones para evitar que se llaman en una compilación comercial de una aplicación. Esta flexibilidad se logra mediante la [_DEBUG](../../c-runtime-library/debug.md) macro; el **_RPT** y **_RPTF** macros solo están disponibles cuando el **_DEBUG** marca es definido. Cuando **_DEBUG** no es está definido, las llamadas a estas macros se quitan durante el preprocesamiento.

El **_RPTW** y **_RPTFW** macros son versiones de caracteres anchos de estas macros. Son como **wprintf** y toman cadenas de caracteres anchos como argumentos.

El **_RPT** macros llamada la [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) función puede generar un informe de depuración con un mensaje de usuario. El **_RPTW** macros llamada la **_CrtDbgReportW** función puede generar el mismo informe con caracteres anchos. El **_RPTF** y **_RPTFW** macros de crean un informe de depuración con el número de archivo y la línea de código fuente donde se llamó la macro de informe, además, para el mensaje de usuario. El mensaje de usuario se crea al sustituir el **arg**[*n*] argumentos a la *formato* de cadena, utilizando las mismas reglas definidas por el [printf](printf-printf-l-wprintf-wprintf-l.md)(función).

**_CrtDbgReport** o **_CrtDbgReportW** genera el informe de depuración y determina sus destinos en función de los modos de informe actual y el archivo definidos para *reportType*. Las funciones [_CrtSetReportMode](crtsetreportmode.md) y [_CrtSetReportFile](crtsetreportfile.md) se usan para definir los destinos de cada tipo de informe.

Si un **_RPT** se llama a macro y ni **_CrtSetReportMode** ni **_CrtSetReportFile** ha sido llama, los mensajes se muestran como se indica a continuación.

|Tipo de informe|Destino de salida|
|-----------------|------------------------|
|**_CRT_WARN**|No se muestra el texto de advertencia.|
|**_CRT_ERROR**|Ventana emergente. Lo mismo que si se hubiera especificado `_CrtSetReportMode(_CRT_ERROR, _CRTDBG_MODE_WNDW);`.|
|**_CRT_ASSERT**|Igual que **_CRT_ERROR**.|

Cuando el destino es una ventana de mensaje de depuración y el usuario elige el **vuelva a intentar** botón, **_CrtDbgReport** o **_CrtDbgReportW** devuelve 1, haciendo que estas macros iniciar el depurador, siempre que se habilita la depuración de just-in-time (JIT). Para obtener más información sobre cómo usar estas macros como mecanismo de control de errores de depuración, vea [Using Macros for Verification and Reporting](/visualstudio/debugger/macros-for-reporting) (Uso de macros para comprobación e informes).

Existen otras dos macros que generan un informe de depuración. La macro [_ASSERT](assert-asserte-assert-expr-macros.md) genera un informe, pero solo cuando su argumento de expresión se evalúa como FALSE. [_ASSERTE](assert-asserte-assert-expr-macros.md) es exactamente like **_ASSERT**, pero incluye la expresión del error en el informe generado.

## <a name="requirements"></a>Requisitos

|Macro|Encabezado necesario|
|-----------|---------------------|
|**_RPT** macros|\<crtdbg.h>|
|**_RPTF** macros|\<crtdbg.h>|
|**_RPTW** macros|\<crtdbg.h>|
|**_RPTFW** macros|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

Aunque se trata de macros y se obtienen incluyendo Crtdbg.h, la aplicación debe vincularse con una de las bibliotecas de depuración, ya que estas macros llaman a otras funciones en tiempo de ejecución.

## <a name="example"></a>Ejemplo

Vea el ejemplo del tema [_ASSERT](assert-asserte-assert-expr-macros.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
