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
ms.openlocfilehash: 7187448b2ba2c9d3ab0399aa3e75ce8d757bfec1
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69496769"
---
# <a name="cdebugreporthook-class"></a>CDebugReportHook (clase)

Utilice esta clase para enviar informes de depuración a una canalización con nombre.

## <a name="syntax"></a>Sintaxis

```
class CDebugReportHook
```

## <a name="members"></a>Miembros

### <a name="public-constructors"></a>Constructores públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Llama a [SetPipeName](#setpipename), [setTimeout](#settimeout)y [SetHook](#sethook).|
|[CDebugReportHook::~CDebugReportHook](#dtor)|Llama a [CDebugReportHook:: RemoveHook](#removehook).|

### <a name="public-methods"></a>Métodos públicos

|NOMBRE|DESCRIPCIÓN|
|----------|-----------------|
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|Estático Función de informes personalizada que se enlaza al proceso de creación de informes de depuración en tiempo de ejecución de C.|
|[CDebugReportHook::RemoveHook](#removehook)|Llame a este método para detener el envío de informes de depuración a la canalización con nombre y restaurar el enlace anterior del informe.|
|[CDebugReportHook::SetHook](#sethook)|Llame a este método para iniciar el envío de informes de depuración a la canalización con nombre.|
|[CDebugReportHook::SetPipeName](#setpipename)|Llame a este método para establecer la máquina y el nombre de la canalización a la que se enviarán los informes de depuración.|
|[CDebugReportHook::SetTimeout](#settimeout)|Llame a este método para establecer el tiempo, en milisegundos, que esta clase esperará a que la canalización con nombre esté disponible.|

## <a name="remarks"></a>Comentarios

Cree una instancia de esta clase en las compilaciones de depuración de los servicios o aplicaciones para enviar informes de depuración a una canalización con nombre. Los informes de depuración se generan llamando a _ [crtdbgreport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) o usando un contenedor para esta función, como las macros [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) y [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) .

El uso de esta clase permite depurar de forma interactiva los componentes que se ejecutan en [estaciones de ventana](/windows/win32/winstation/window-stations)no interactivas.

Tenga en cuenta que los informes de depuración se envían mediante el contexto de seguridad subyacente del subproceso. La suplantación está deshabilitada temporalmente para que los informes de depuración puedan verse en situaciones en las que se está llevando a cabo la suplantación de usuarios con pocos privilegios, como en las aplicaciones Web.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlutil. h

##  <a name="cdebugreporthook"></a>  CDebugReportHook::CDebugReportHook

Llama a [SetPipeName](#setpipename), [setTimeout](#settimeout)y [SetHook](#sethook).

```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```

### <a name="parameters"></a>Parámetros

*szMachineName*<br/>
Nombre del equipo al que se debe enviar la salida de depuración. Tiene como valor predeterminado el equipo local.

*szPipeName*<br/>
Nombre de la canalización con nombre a la que se debe enviar la salida de depuración.

*dwTimeout*<br/>
El tiempo, en milisegundos, que esta clase esperará a que la canalización con nombre esté disponible.

##  <a name="dtor"></a>  CDebugReportHook::~CDebugReportHook

Llama a [CDebugReportHook:: RemoveHook](#removehook).

```
~CDebugReportHook() throw();
```

##  <a name="cdebugreporthookproc"></a>  CDebugReportHook::CDebugReportHookProc

Función de informes personalizada que se enlaza al proceso de creación de informes de depuración en tiempo de ejecución de C.

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
Cadena de mensaje.

*returnValue*<br/>
Valor que debe devolver _ [crtdbgreport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).

### <a name="return-value"></a>Valor devuelto

Devuelve FALSE si el enlace controla el mensaje en cuestión por completo para que no sea necesario ningún otro informe. Devuelve true si `_CrtDbgReport` debe notificar el mensaje de la manera normal.

### <a name="remarks"></a>Comentarios

La función de generación de informes intenta abrir la canalización con nombre y comunicarse con el proceso en el otro extremo. Si la canalización está ocupada, la función de generación de informes esperará hasta que la canalización sea gratuita o hasta que expire el tiempo de espera. El tiempo de espera se puede establecer mediante el constructor o una llamada a [CDebugReportHook:: setTimeout](#settimeout).

El código de esta función se ejecuta en el contexto de seguridad subyacente del subproceso que realiza la llamada, es decir, se deshabilita la suplantación mientras dure esta función.

##  <a name="removehook"></a>  CDebugReportHook::RemoveHook

Llame a este método para detener el envío de informes de depuración a la canalización con nombre y restaurar el enlace anterior del informe.

```
void RemoveHook() throw();
```

### <a name="remarks"></a>Comentarios

Llama a [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) para restaurar el enlace de informe anterior.

##  <a name="sethook"></a>  CDebugReportHook::SetHook

Llame a este método para iniciar el envío de informes de depuración a la canalización con nombre.

```
void SetHook() throw();
```

### <a name="remarks"></a>Comentarios

Llama a [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) para que los informes de depuración se enruten a través de [CDebugReportHookProc](#cdebugreporthookproc) a la canalización con nombre. Esta clase realiza un seguimiento del enlace del informe anterior para que se pueda restaurar cuando se llama a [RemoveHook](#removehook) .

##  <a name="setpipename"></a>  CDebugReportHook::SetPipeName

Llame a este método para establecer la máquina y el nombre de la canalización a la que se enviarán los informes de depuración.

```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```

### <a name="parameters"></a>Parámetros

*szMachineName*<br/>
Nombre del equipo al que se debe enviar la salida de depuración.

*szPipeName*<br/>
Nombre de la canalización con nombre a la que se debe enviar la salida de depuración.

### <a name="return-value"></a>Valor devuelto

Devuelve TRUE si es correcto, FALSE en caso de error.

##  <a name="settimeout"></a>  CDebugReportHook::SetTimeout

Llame a este método para establecer el tiempo, en milisegundos, que esta clase esperará a que la canalización con nombre esté disponible.

```
void SetTimeout(DWORD dwTimeout);
```

### <a name="parameters"></a>Parámetros

*dwTimeout*<br/>
El tiempo, en milisegundos, que esta clase esperará a que la canalización con nombre esté disponible.

## <a name="see-also"></a>Vea también

[Clases](../../atl/reference/atl-classes.md)
