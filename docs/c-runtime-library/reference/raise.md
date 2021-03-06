---
title: raise
ms.date: 4/2/2020
api_name:
- raise
- _o_raise
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
- api-ms-win-crt-runtime-l1-1-0.dll
- api-ms-win-crt-private-l1-1-0.dll
api_type:
- DLLExport
topic_type:
- apiref
f1_keywords:
- Raise
helpviewer_keywords:
- signals, sending to executing programs
- raise function
- signals
- programs [C++], sending signals to executing programs
ms.openlocfilehash: 81b92404603820948a384b6ad33421251a27c13c
ms.sourcegitcommit: 5a069c7360f75b7c1cf9d4550446ec2fa2eb2293
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2020
ms.locfileid: "82919552"
---
# <a name="raise"></a>raise

Envía una señal al programa en ejecución.

> [!NOTE]
> No use este método para cerrar una aplicación Microsoft Store, excepto en escenarios de prueba o depuración. No se permiten las formas de cerrar una aplicación de la tienda mediante programación o la interfaz de usuario de acuerdo con las [directivas de Microsoft Store](/legal/windows/agreements/store-policies). Para obtener más información, consulte el ciclo de vida de las [aplicaciones para UWP](/windows/uwp/launch-resume/app-lifecycle).

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

## <a name="remarks"></a>Observaciones

La función **raise** envía *sig* al programa en ejecución. Si una llamada anterior a **signal** ha instalado una función de control de señales para *sig*, **raise** ejecuta esa función. Si no se ha instalado ninguna función de controlador, se lleva a cabo la acción predeterminada asociada al valor de señal *sig*, como se indica a continuación.

|Señal|Significado|Default|
|------------|-------------|-------------|
|**SIGABRT**|Terminación anómala|Finaliza el programa de llamada con el código de salida 3|
|**SIGFPE**|Error de punto flotante|Finaliza el programa de llamada|
|**SIGILL**|Instrucción no válida|Finaliza el programa de llamada|
|**SIGINT**|Interrupción de CTRL+C|Finaliza el programa de llamada|
|**SIGSEGV**|Acceso no válido a almacenamiento|Finaliza el programa de llamada|
|**SIGTERM**|Solicitud de finalización enviada al programa|Omite la señal|

Si el argumento no es una señal válida según lo especificado anteriormente, se invoca al controlador de parámetros no válidos, como se describe en [Validación de parámetros](../../c-runtime-library/parameter-validation.md). Si no se controla, la función establece **errno** en **EINVAL** y devuelve un valor distinto de cero.

De forma predeterminada, el ámbito de este estado global de esta función es la aplicación. Para cambiar esto, vea [estado global en CRT](../global-state.md).

## <a name="requirements"></a>Requisitos

|Rutina|Encabezado necesario|
|-------------|---------------------|
|**raise**|\<signal.h>|

Para obtener información adicional sobre compatibilidad, consulte [Compatibilidad](../../c-runtime-library/compatibility.md).

## <a name="see-also"></a>Consulta también

[Control de proceso y entorno](../../c-runtime-library/process-and-environment-control.md)<br/>
[aborta](abort.md)<br/>
[signal](signal.md)<br/>
