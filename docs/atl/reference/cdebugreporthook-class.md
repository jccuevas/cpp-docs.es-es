---
title: CDebugReportHook (clase)
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
ms.openlocfilehash: a7c5993d1b96daaa73e7fc9509c93e66daed77f3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62245932"
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook (clase)

Utilice esta clase para enviar informes de depuración a una canalización con nombre.

## <a name="syntax"></a>Sintaxis

```
class CDebugReportHook
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|Name|Descripción|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Las llamadas [SetPipeName](#setpipename), [SetTimeout](#settimeout), y [SetHook](#sethook).|
|[CDebugReportHook::~CDebugReportHook](#dtor)|Las llamadas [CDebugReportHook::RemoveHook](#removehook).|

### <a name="public-methods"></a>Métodos públicos

|Name|Descripción|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Estático) La función de supervisión personalizada que está enlazada con el tiempo de ejecución de C depurar el proceso de generación de informes.|
|[CDebugReportHook::RemoveHook](#removehook)|Llame a este método para detener el envío de informes de depuración a la canalización con nombre y restaurar el enlace de informe anterior.|
|[CDebugReportHook::SetHook](#sethook)|Llame a este método para empezar a enviar informes de depuración a la canalización con nombre.|
|[CDebugReportHook::SetPipeName](#setpipename)|Llame a este método para establecer la máquina y el nombre de la canalización a la que se enviarán los informes de depuración.|
|[CDebugReportHook::SetTimeout](#settimeout)|Llame a este método para establecer el tiempo en milisegundos que esperará la canalización con nombre esté disponible a que esta clase.|

## <a name="remarks"></a>Comentarios

Cree una instancia de esta clase en las compilaciones de depuración de los servicios o aplicaciones para enviar informes de depuración a una canalización con nombre. Informes de depuración se generan mediante una llamada a [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) o mediante un contenedor para esta función, como el [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) y [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) macros.

Uso de esta clase le permite depurar de forma interactiva los componentes que se ejecutan no interactivo [estaciones de ventana](/windows/desktop/winstation/window-stations).

Tenga en cuenta que los informes de depuración se envían mediante el contexto de seguridad subyacente del subproceso. Suplantación está deshabilitada temporalmente para que se puedan ver los informes de depuración en situaciones donde la suplantación de usuarios con pocos privilegios está teniendo lugar, como en las aplicaciones web.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil.h

##  <a name="cdebugreporthook"></a>  CDebugReportHook::CDebugReportHook

Las llamadas [SetPipeName](#setpipename), [SetTimeout](#settimeout), y [SetHook](#sethook).

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
El tiempo en milisegundos que esperará la canalización con nombre esté disponible a que esta clase.

##  <a name="dtor"></a>  CDebugReportHook::~CDebugReportHook

Las llamadas [CDebugReportHook::RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>  CDebugReportHook::CDebugReportHookProc

La función de supervisión personalizada que está enlazada con el tiempo de ejecución de C depurar el proceso de generación de informes.

```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```

### <a name="parameters"></a>Parámetros

*reportType*<br/>
El tipo de informe (_CRT_WARN, _CRT_ERROR o _CRT_ASSERT).

*message*<br/>
La cadena de mensaje.

*returnValue*<br/>
El valor que debe devolver [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE si el enlace encarga el mensaje en cuestión por completo para que se requiera ningún informe. Devuelve TRUE si `_CrtDbgReport` debe notificar el mensaje de la manera normal.

### <a name="remarks"></a>Comentarios

La función de creación de informes intenta abrir la canalización con nombre y comunicarse con el proceso en el otro extremo. Si la canalización está ocupada, la función de creación de informes esperará hasta que la canalización está disponible o expire el tiempo de espera. El tiempo de espera puede establecerse mediante el constructor o una llamada a [CDebugReportHook::SetTimeout](#settimeout).

El código de esta función se ejecuta en el contexto de seguridad subyacente del subproceso que realiza la llamada, es decir, la suplantación está deshabilitada para la duración de esta función.

##  <a name="removehook"></a>  CDebugReportHook::RemoveHook

Llame a este método para detener el envío de informes de depuración a la canalización con nombre y restaurar el enlace de informe anterior.

```
void RemoveHook() throw();
```

### <a name="remarks"></a>Comentarios

Las llamadas [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) para restaurar el enlace de informe anterior.

##  <a name="sethook"></a>  CDebugReportHook::SetHook

Llame a este método para empezar a enviar informes de depuración a la canalización con nombre.

```
void SetHook() throw();
```

### <a name="remarks"></a>Comentarios

Las llamadas [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) enruta a través de informes de depuración [CDebugReportHookProc](#cdebugreporthookproc) a la canalización con nombre. Esta clase realiza un seguimiento del enlace de informe anterior para que pueda restaurar cuando [RemoveHook](#removehook) se llama.

##  <a name="setpipename"></a>  CDebugReportHook::SetPipeName

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

Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.

##  <a name="settimeout"></a>  CDebugReportHook::SetTimeout

Llame a este método para establecer el tiempo en milisegundos que esperará la canalización con nombre esté disponible a que esta clase.

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parámetros

*dwTimeout*<br/>
El tiempo en milisegundos que esperará la canalización con nombre esté disponible a que esta clase.

## <a name="see-also"></a>Vea también

[Clases](../../atl/reference/atl-classes.md)
