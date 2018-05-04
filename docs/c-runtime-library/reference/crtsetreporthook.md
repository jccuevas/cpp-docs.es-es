---
title: _CrtSetReportHook | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
apiname:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
dev_langs:
- C++
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1ef76fe0b7befb99b5bf0e8bb69fa1a1229782de
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="crtsetreporthook"></a>_CrtSetReportHook

Instala una función de generación de informes definida por el cliente enlazándola al proceso de creación de informes de depuración en tiempo de ejecución de C (solo versión de depuración).

## <a name="syntax"></a>Sintaxis

```C
_CRT_REPORT_HOOK _CrtSetReportHook(
   _CRT_REPORT_HOOK reportHook
);
```

### <a name="parameters"></a>Parámetros

*reportHook*<br/>
Nueva función de creación de informes definida por el cliente que se va a enlazar al proceso de creación de informes de depuración en tiempo de ejecución de C.

## <a name="return-value"></a>Valor devuelto

Devuelve la función de creación de informes definida por el cliente anterior.

## <a name="remarks"></a>Comentarios

**_CrtSetReportHook** permite que una aplicación usar su propia reporting función en la biblioteca de depuración en tiempo de ejecución de C proceso de notificación. Por consiguiente, siempre que se llame a [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) para generar un informe de depuración, se llama primero a la función de creación de informes de la aplicación. Esta funcionalidad permite a una aplicación realizar operaciones como el filtrado de informes de depuración para que pueda centrarse en los tipos de asignación concretos o enviar un informe a destinos no están disponibles mediante el uso de **_CrtDbgReport**. Cuando [_DEBUG](../../c-runtime-library/debug.md) no está definido, las llamadas a **_CrtSetReportHook** se quitan durante el preprocesamiento.

Para obtener una versión más sólida de **_CrtSetReportHook**, consulte [_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md).

El **_CrtSetReportHook** función instala la nueva función especificada en para generar informes definida por el cliente *reportHook* y devuelve el enlace definido por el cliente anterior. En el ejemplo siguiente se muestra cómo se deben crear prototipos de un enlace de informe definido por el cliente:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

donde *reportType* es el tipo de informe de depuración (**_CRT_WARN**, **_CRT_ERROR**, o **_CRT_ASSERT**), *mensaje* es el mensaje de usuario totalmente ensamblado de depuración para poder estar contenidos en el informe, y **returnValue** el valor especificado por definido por el cliente informa de función que debe devolver **_ CrtDbgReport**. Para obtener una descripción completa de los tipos de informe disponibles, consulte la función [_CrtSetReportMode](crtsetreportmode.md).

Si la función de creación de informes definida por el cliente controla completamente el mensaje de depuración, que no se requiera ningún informe posterior, la función debe devolver **TRUE**. Cuando la función devuelve **FALSE**, **_CrtDbgReport** se invoca para generar el informe de depuración mediante la configuración actual para el tipo de informe, el modo y el archivo. Además, especificando el **_CrtDbgReport** devolver valor de **returnValue**, la aplicación también puede controlar si se produce una interrupción de depuración. Para obtener una descripción completa de cómo se configura y se genera el informe de depuración, consulte **_CrtSetReportMode**, [_CrtSetReportFile](crtsetreportfile.md), y **_CrtDbgReport**.

Para obtener más información sobre cómo usar otras funciones con capacidad de enlace en tiempo de ejecución y cómo escribir funciones de enlace definidas por el cliente, consulte [Creación de funciones de enlace de depuración](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> Si la aplicación se compila con **/CLR** y la función de creación de informes se llama después de que la aplicación se ha cerrado principal, el CLR iniciará una excepción si la función de creación de informes llama a las funciones de CRT.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**_CrtSetReportHook**|\<crtdbg.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="libraries"></a>Bibliotecas

Solo versiones de depuración de las [bibliotecas en tiempo de ejecución de C](../../c-runtime-library/crt-library-features.md).

## <a name="see-also"></a>Vea también

[Rutinas de depuración](../../c-runtime-library/debug-routines.md)<br/>
[_CrtGetReportHook](crtgetreporthook.md)<br/>
