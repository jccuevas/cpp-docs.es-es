---
title: _CrtSetReportHook
ms.date: 11/04/2016
api_name:
- _CrtSetReportHook
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
- _CrtSetReportHook
- CrtSetReportHook
helpviewer_keywords:
- CrtSetReportHook function
- _CrtSetReportHook function
ms.assetid: 1ae7c64f-8c84-4797-9574-b59f00f7a509
ms.openlocfilehash: 77c1e499c66a76027e872783e256754ef72e465d
ms.sourcegitcommit: f19474151276d47da77cdfd20df53128fdcc3ea7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/12/2019
ms.locfileid: "70938512"
---
# <a name="_crtsetreporthook"></a>_CrtSetReportHook

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

**_CrtSetReportHook** permite que una aplicación use su propia función de creación de informes en el proceso de informes de la biblioteca de depuración en tiempo de ejecución de C. Por consiguiente, siempre que se llame a [_CrtDbgReport](crtdbgreport-crtdbgreportw.md) para generar un informe de depuración, se llama primero a la función de creación de informes de la aplicación. Esta funcionalidad permite que una aplicación realice operaciones como el filtrado de informes de depuración para que pueda centrarse en determinados tipos de asignación o enviar un informe a destinos no disponibles mediante _ **crtdbgreport**. Cuando no se define [_ Debug](../../c-runtime-library/debug.md) , las llamadas a **_CrtSetReportHook** se quitan durante el preprocesamiento.

Para obtener una versión más sólida de **_CrtSetReportHook**, consulte [_CrtSetReportHook2](crtsetreporthook2-crtsetreporthookw2.md).

La función **_CrtSetReportHook** instala la nueva función de creación de informes definida por el cliente especificada en *reportHook* y devuelve el enlace definido por el cliente anterior. En el ejemplo siguiente se muestra cómo se deben crear prototipos de un enlace de informe definido por el cliente:

```C
int YourReportHook( int reportType, char *message, int *returnValue );
```

donde *reportType* es el tipo de informe de depuración ( **_CRT_WARN**, **_CRT_ERROR**o **_CRT_ASSERT**), *Message* es el mensaje de usuario de depuración totalmente ensamblado que se va a incluir en el informe y **ReturnValue** es el valor. especificado por la función de creación de informes definida por el cliente que debe devolver _ **crtdbgreport**. Para obtener una descripción completa de los tipos de informe disponibles, consulte la función [_CrtSetReportMode](crtsetreportmode.md).

Si la función de creación de informes definida por el cliente controla completamente el mensaje de depuración para que no sea necesario ningún otro informe, la función debe devolver **true**. Cuando la función devuelve **false**, se llama a _ **crtdbgreport** para generar el informe de depuración con la configuración actual del tipo de informe, el modo y el archivo. Además, al especificar el valor devuelto de _ **crtdbgreport** en **ReturnValue**, la aplicación también puede controlar si se produce una interrupción de depuración. Para obtener una descripción completa de cómo se configura y genera el informe de depuración, vea _ **crtsetreportmode**, [_CrtSetReportFile](crtsetreportfile.md)y _ **crtdbgreport**.

Para obtener más información sobre cómo usar otras funciones con capacidad de enlace en tiempo de ejecución y cómo escribir funciones de enlace definidas por el cliente, consulte [Creación de funciones de enlace de depuración](/visualstudio/debugger/debug-hook-function-writing).

> [!NOTE]
> Si la aplicación se compila con **/CLR** y se llama a la función de generación de informes después de que la aplicación haya salido de Main, CLR producirá una excepción si la función de creación de informes llama a las funciones de CRT.

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
