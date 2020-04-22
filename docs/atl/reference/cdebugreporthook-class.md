---
title: Clase CDebugReportHook
ms.date: 11/04/2016
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
ms.openlocfilehash: 8380556bbe007326156bf0ec0eefc23052e8e056
ms.sourcegitcommit: 7a6116e48c3c11b97371b8ae4ecc23adce1f092d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/22/2020
ms.locfileid: "81747721"
---
# <a name="cdebugreporthook-class"></a>Clase CDebugReportHook

Utilice esta clase para enviar informes de depuración a una canalización con nombre.

## <a name="syntax"></a>Sintaxis

```
class CDebugReportHook
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Llama a [SetPipeName](#setpipename), [SetTimeout](#settimeout)y [SetHook](#sethook).|
|[CDebugReportHook::-CDebugReportHook](#dtor)|Llama a [CDebugReportHook::RemoveHook](#removehook).|

### <a name="public-methods"></a>Métodos públicos

|Nombre|Descripción|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Estático) La función de informes personalizada que se enlaza en el proceso de informes de depuración en tiempo de ejecución de C.|
|[CDebugReportHook::RemoveHook](#removehook)|Llame a este método para dejar de enviar informes de depuración a la canalización con nombre y restaurar el enlace de informe anterior.|
|[CDebugReportHook::SetHook](#sethook)|Llame a este método para empezar a enviar informes de depuración a la canalización con nombre.|
|[CDebugReportHook::SetPipeName](#setpipename)|Llame a este método para establecer la máquina y el nombre de la canalización a la que se enviarán los informes de depuración.|
|[CDebugReportHook::SetTimeout](#settimeout)|Llame a este método para establecer el tiempo en milisegundos que esta clase esperará a que la canalización con nombre esté disponible.|

## <a name="remarks"></a>Observaciones

Cree una instancia de esta clase en compilaciones de depuración de sus servicios o aplicaciones para enviar informes de depuración a una canalización con nombre. Los informes de depuración se generan llamando a [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) o mediante un contenedor para esta función, como las macros [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) y [ATLASSERT.](debugging-and-error-reporting-macros.md#atlassert)

El uso de esta clase le permite depurar de forma interactiva los componentes que se ejecutan en estaciones de ventana no [interactivas.](/windows/win32/winstation/window-stations)

Tenga en cuenta que los informes de depuración se envían mediante el contexto de seguridad subyacente del subproceso. La suplantación se deshabilita temporalmente para que los informes de depuración se puedan ver en situaciones en las que se está produciendo la suplantación de usuarios con privilegios bajos, como en aplicaciones web.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

## <a name="cdebugreporthookcdebugreporthook"></a><a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook

Llama a [SetPipeName](#setpipename), [SetTimeout](#settimeout)y [SetHook](#sethook).

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Parámetros

*szMachineName*<br/>
El nombre de la máquina a la que se debe enviar la salida de depuración. El valor predeterminado es el equipo local.

*szPipeName*<br/>
El nombre de la canalización con nombre a la que se debe enviar la salida de depuración.

*dwTimeout*<br/>
El tiempo en milisegundos que esta clase esperará a que la canalización con nombre esté disponible.

## <a name="cdebugreporthookcdebugreporthook"></a><a name="dtor"></a>CDebugReportHook::-CDebugReportHook

Llama a [CDebugReportHook::RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

## <a name="cdebugreporthookcdebugreporthookproc"></a><a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc

La función de informes personalizada que se enlaza en el proceso de informes de depuración en tiempo de ejecución de C.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>Parámetros

*reportType*<br/>
El tipo del informe (_CRT_WARN, _CRT_ERROR o _CRT_ASSERT).

*message*<br/>
Cadena del mensaje.

*returnValue*<br/>
El valor que debe devolver [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE si el enlace controla completamente el mensaje en cuestión para que no se requieran más informes. Devuelve TRUE `_CrtDbgReport` si debe notificar el mensaje de la manera normal.

### <a name="remarks"></a>Observaciones

La función de notificación intenta abrir la canalización con nombre y comunicarse con el proceso en el otro extremo. Si la canalización está ocupada, la función de informes esperará hasta que la canalización esté libre o el tiempo de espera expire. El constructor puede establecer el tiempo de espera o una llamada a [CDebugReportHook::SetTimeout](#settimeout).

El código de esta función se ejecuta en el contexto de seguridad subyacente del subproceso que realiza la llamada, es decir, la suplantación está deshabilitada durante la duración de esta función.

## <a name="cdebugreporthookremovehook"></a><a name="removehook"></a>CDebugReportHook::RemoveHook

Llame a este método para dejar de enviar informes de depuración a la canalización con nombre y restaurar el enlace de informe anterior.

```cpp
void RemoveHook() throw();
```

### <a name="remarks"></a>Observaciones

Las llamadas [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) para restaurar el enlace de informe anterior.

## <a name="cdebugreporthooksethook"></a><a name="sethook"></a>CDebugReportHook::SetHook

Llame a este método para empezar a enviar informes de depuración a la canalización con nombre.

```cpp
void SetHook() throw();
```

### <a name="remarks"></a>Observaciones

Las [llamadas _CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) tener informes de depuración enrutados a través de [CDebugReportHookProc](#cdebugreporthookproc) a la canalización con nombre. Esta clase realiza un seguimiento del enlace de informe anterior para que se pueda restaurar cuando se llama a [RemoveHook.](#removehook)

## <a name="cdebugreporthooksetpipename"></a><a name="setpipename"></a>CDebugReportHook::SetPipeName

Llame a este método para establecer la máquina y el nombre de la canalización a la que se enviarán los informes de depuración.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Parámetros

*szMachineName*<br/>
El nombre de la máquina a la que se debe enviar la salida de depuración.

*szPipeName*<br/>
El nombre de la canalización con nombre a la que se debe enviar la salida de depuración.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE en caso de éxito, FALSE en caso de error.

## <a name="cdebugreporthooksettimeout"></a><a name="settimeout"></a>CDebugReportHook::SetTimeout

Llame a este método para establecer el tiempo en milisegundos que esta clase esperará a que la canalización con nombre esté disponible.

```cpp
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parámetros

*dwTimeout*<br/>
El tiempo en milisegundos que esta clase esperará a que la canalización con nombre esté disponible.

## <a name="see-also"></a>Vea también

[Clases](../../atl/reference/atl-classes.md)
