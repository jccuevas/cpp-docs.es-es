---
title: Clase CDebugReportHook | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHook
- ATLUTIL/ATL::CDebugReportHook::CDebugReportHookProc
- ATLUTIL/ATL::CDebugReportHook::RemoveHook
- ATLUTIL/ATL::CDebugReportHook::SetHook
- ATLUTIL/ATL::CDebugReportHook::SetPipeName
- ATLUTIL/ATL::CDebugReportHook::SetTimeout
dev_langs:
- C++
helpviewer_keywords:
- CDebugReportHook class
ms.assetid: 798076c3-6e63-4286-83b8-aa1bbcd0c20c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d84b2da8a347833513e0725695bb9d2bacd2951d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Llamadas [SetPipeName](#setpipename), [SetTimeout](#settimeout), y [SetHook](#sethook).|  
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|Llamadas [CDebugReportHook::RemoveHook](#removehook).|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Estático) La función de supervisión personalizada que se enlaza al proceso de notificación de depuración en tiempo de ejecución C.|  
|[CDebugReportHook::RemoveHook](#removehook)|Llamar a este método para detener el envío de informes de depuración a la canalización con nombre y restaurar el enlace de informe anterior.|  
|[CDebugReportHook::SetHook](#sethook)|Llame a este método para empezar a enviar informes de depuración a la canalización con nombre.|  
|[CDebugReportHook::SetPipeName](#setpipename)|Llame a este método para establecer la máquina y el nombre de la canalización a la que se enviarán los informes de depuración.|  
|[CDebugReportHook::SetTimeout](#settimeout)|Llamar a este método para establecer el tiempo en milisegundos que esta clase esperará a que la canalización con nombre hasta que esté disponible.|  
  
## <a name="remarks"></a>Comentarios  
 Crear una instancia de esta clase en compilaciones de depuración de los servicios o aplicaciones para enviar informes de depuración a una canalización con nombre. Informes de depuración se generan mediante una llamada a [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) o de un contenedor para esta función como el [ATLTRACE](debugging-and-error-reporting-macros.md#atltrace) y [ATLASSERT](debugging-and-error-reporting-macros.md#atlassert) macros.  
  
 Uso de esta clase le permite depurar de forma interactiva los componentes que se ejecutan no interactivo [estaciones de ventana](http://msdn.microsoft.com/library/windows/desktop/ms687096).  
  
 Tenga en cuenta que se envían informes de depuración utilizando el contexto de seguridad subyacente del subproceso. Suplantación está deshabilitada temporalmente para que puedan ver informes de depuración en situaciones donde la suplantación de usuarios con pocos privilegios está teniendo lugar, como en las aplicaciones web.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="cdebugreporthook"></a>  CDebugReportHook::CDebugReportHook  
 Llamadas [SetPipeName](#setpipename), [SetTimeout](#settimeout), y [SetHook](#sethook).  
  
```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `szMachineName`  
 El nombre de la máquina a la que se debe enviar el resultado de depuración. El valor predeterminado es el equipo local.  
  
 `szPipeName`  
 El nombre de la canalización con nombre a la que se debe enviar el resultado de depuración.  
  
 `dwTimeout`  
 El tiempo en milisegundos que esta clase esperará a que la canalización con nombre hasta que esté disponible.  
  
##  <a name="dtor"></a>  CDebugReportHook:: ~ CDebugReportHook  
 Llamadas [CDebugReportHook::RemoveHook](#removehook).  
  
```
~CDebugReportHook() throw();
```  
  
##  <a name="cdebugreporthookproc"></a>  CDebugReportHook::CDebugReportHookProc  
 La función de supervisión personalizada que se enlaza al proceso de notificación de depuración en tiempo de ejecución C.  
  
```
static int __cdecl CDebugReportHookProc(
    int reportType,
    char* message,
    int* returnValue) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `reportType`  
 El tipo de informe (_CRT_WARN, _CRT_ERROR o _CRT_ASSERT).  
  
 `message`  
 La cadena de mensaje.  
  
 *ReturnValue*  
 El valor que debe devolver [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve FALSE si el enlace encarga el mensaje en cuestión por completo para que se requiera ningún informe. Devuelve TRUE si `_CrtDbgReport` debería notificar el mensaje de la forma habitual.  
  
### <a name="remarks"></a>Comentarios  
 La función de creación de informes intenta abrir la canalización con nombre y comunicarse con el proceso en el otro extremo. Si la canalización está ocupada, la función de creación de informes esperará hasta que la canalización está disponible o se agota el tiempo de espera. El tiempo de espera se puede establecer en el constructor o una llamada a [CDebugReportHook::SetTimeout](#settimeout).  
  
 El código de esta función se ejecuta en el contexto de seguridad subyacente del subproceso que realiza la llamada, es decir, la suplantación está deshabilitada para la duración de esta función.  
  
##  <a name="removehook"></a>  CDebugReportHook::RemoveHook  
 Llamar a este método para detener el envío de informes de depuración a la canalización con nombre y restaurar el enlace de informe anterior.  
  
```
void RemoveHook() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) para restaurar el enlace de informe anterior.  
  
##  <a name="sethook"></a>  CDebugReportHook::SetHook  
 Llame a este método para empezar a enviar informes de depuración a la canalización con nombre.  
  
```
void SetHook() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) disponer de informes de depuración que se enrutan a través de [CDebugReportHookProc](#cdebugreporthookproc) a la canalización con nombre. Esta clase realiza un seguimiento del enlace de informe anterior para que pueda restaurar cuando [RemoveHook](#removehook) se llama.  
  
##  <a name="setpipename"></a>  CDebugReportHook::SetPipeName  
 Llame a este método para establecer la máquina y el nombre de la canalización a la que se enviarán los informes de depuración.  
  
```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `szMachineName`  
 El nombre de la máquina a la que se debe enviar el resultado de depuración.  
  
 `szPipeName`  
 El nombre de la canalización con nombre a la que se debe enviar el resultado de depuración.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="settimeout"></a>  CDebugReportHook::SetTimeout  
 Llamar a este método para establecer el tiempo en milisegundos que esta clase esperará a que la canalización con nombre hasta que esté disponible.  
  
```
void SetTimeout(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwTimeout`  
 El tiempo en milisegundos que esta clase esperará a que la canalización con nombre hasta que esté disponible.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../atl/reference/atl-classes.md)
