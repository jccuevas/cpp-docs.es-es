---
title: raise
ms.date: 1/02/2018
apiname:
- raise
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
- api-ms-win-crt-runtime-l1-1-0.dll
apitype: DLLExport
f1_keywords:
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: 68d1cc653b955e607648e4d30562d2b77e3520e2
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50638118"
---
# <a name="raise"></a>raise

Envía una señal al programa en ejecución.

> [!NOTE]
> No utilice este método para cerrar una aplicación de Microsoft Store, excepto en las pruebas o escenarios de depuración. No se permiten formas mediante programación o con la interfaz de usuario para cerrar una aplicación de Store según la [las directivas de Microsoft Store](/legal/windows/agreements/store-policies). Para obtener más información, consulte [ciclo de vida de aplicación UWP](/windows/uwp/launch-resume/app-lifecycle).

## <a name="syntax"></a>Sintaxis

```C
int raise(
   int sig
);
```

### <a name="parameters"></a>Parámetros

*sig*<br/>
Señal que se va a producir.

## <a name="return-value"></a>Valor devuelto

Si se ejecuta correctamente, **raise** devuelve 0. De lo contrario, devuelve un valor distinto de cero.

## <a name="remarks"></a>Comentarios

La función **raise** envía *sig* al programa en ejecución. Si una llamada anterior a **signal** ha instalado una función de control de señales para *sig*, **raise** ejecuta esa función. Si no se ha instalado ninguna función de controlador, se lleva a cabo la acción predeterminada asociada al valor de señal *sig*, como se indica a continuación.

|Señal|Significado|Default|
|------------|-------------|-------------|
|**SIGABRT**|Terminación anómala|Finaliza el programa de llamada con el código de salida 3|
|**SIGFPE**|Error de punto flotante|Finaliza el programa de llamada|
|**SIGILL**|Instrucción no válida|Finaliza el programa de llamada|
|**SIGINT**|Interrupción de CTRL+C|Finaliza el programa de llamada|
|**SIGSEGV**|Acceso no válido a almacenamiento|Finaliza el programa de llamada|
|**SIGTERM**|Solicitud de finalización enviada al programa|Omite la señal|

Si el argumento no es una señal válida según lo especificado anteriormente, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si no controla, la función establece **errno** a **EINVAL** y devuelve un valor distinto de cero.

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**raise**|\<signal.h>|

Para obtener más información sobre compatibilidad, vea [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Vea también

[Control de proceso y de entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[abort](abort.md)<br/>
[signal](signal.md)<br/>
