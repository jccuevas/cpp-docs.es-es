---
title: Clase CDebugReportHook | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
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
caps.latest.revision: 22
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 632167d4f78ef930673450d6d087f32e91b6541f
ms.lasthandoff: 02/24/2017

---
# <a name="cdebugreporthook-class"></a>CDebugReportHook (clase)
Utilice esta clase para enviar informes de depuración a una canalización con nombre.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CDebugReportHook
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHook](#cdebugreporthook)|Llamadas [SetPipeName](#setpipename), [SetTimeout](#settimeout), y [SetHook](#sethook).|  
|[CDebugReportHook:: ~ CDebugReportHook](#dtor)|Llamadas [CDebugReportHook::RemoveHook](#removehook).|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CDebugReportHook::CDebugReportHookProc](#cdebugreporthookproc)|(Estático) La función de supervisión personalizada que se enlaza en tiempo de ejecución de C depurar el proceso de creación de informes.|  
|[CDebugReportHook::RemoveHook](#removehook)|Llamar a este método para dejar de enviar informes de depuración a la canalización con nombre y restaurar el enlace de informe anterior.|  
|[CDebugReportHook::SetHook](#sethook)|Llame a este método para empezar a enviar informes de depuración a la canalización con nombre.|  
|[CDebugReportHook::SetPipeName](#setpipename)|Llame a este método para establecer la máquina y el nombre de la canalización a la que se enviarán informes de depuración.|  
|[CDebugReportHook::SetTimeout](#settimeout)|Llamar a este método para establecer el tiempo en milisegundos que esperará esta clase para que la canalización con nombre esté disponible.|  
  
## <a name="remarks"></a>Comentarios  
 Cree una instancia de esta clase en compilaciones de depuración de los servicios o aplicaciones para enviar informes de depuración a una canalización con nombre. Los informes de depuración generados mediante una llamada a [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md) o el uso de un contenedor de esta función como el [ATLTRACE](http://msdn.microsoft.com/library/c796baa5-e2b9-4814-a27d-d800590b102e) y [ATLASSERT](http://msdn.microsoft.com/library/98e3e0fc-77e2-499b-a6f6-b17a21c6fbd3) macros.  
  
 Uso de esta clase le permite depurar de forma interactiva los componentes que se ejecutan no interactivo [estaciones de ventana](http://msdn.microsoft.com/library/windows/desktop/ms687096).  
  
 Tenga en cuenta que los informes de depuración se envían mediante el contexto de seguridad subyacente del subproceso. La suplantación está deshabilitada temporalmente para que se pueden ver informes de depuración en situaciones donde la suplantación de usuarios con pocos privilegios está teniendo lugar, como en aplicaciones web.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlutil.h  
  
##  <a name="cdebugreporthook"></a>CDebugReportHook::CDebugReportHook  
 Llamadas [SetPipeName](#setpipename), [SetTimeout](#settimeout), y [SetHook](#sethook).  
  
```
CDebugReportHook(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe",
    DWORD dwTimeout = 20000) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `szMachineName`  
 El nombre del equipo al que se debe enviar el resultado de depuración. El valor predeterminado es el equipo local.  
  
 `szPipeName`  
 El nombre de la canalización con nombre al que se debe enviar el resultado de depuración.  
  
 `dwTimeout`  
 El tiempo en milisegundos que esperará esta clase para que la canalización con nombre esté disponible.  
  
##  <a name="dtor"></a>CDebugReportHook:: ~ CDebugReportHook  
 Llamadas [CDebugReportHook::RemoveHook](#removehook).  
  
```
~CDebugReportHook() throw();
```  
  
##  <a name="cdebugreporthookproc"></a>CDebugReportHook::CDebugReportHookProc  
 La función de supervisión personalizada que se enlaza en tiempo de ejecución de C depurar el proceso de creación de informes.  
  
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
  
 *returnValue*  
 El valor que se debe devolver [_CrtDbgReport](../../c-runtime-library/reference/crtdbgreport-crtdbgreportw.md).  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve FALSE si el enlace encarga el mensaje en cuestión completamente para que se requiera ningún informe. Devuelve TRUE si `_CrtDbgReport` debe notificar el mensaje de la manera normal.  
  
### <a name="remarks"></a>Comentarios  
 La función de informes intenta abrir la canalización con nombre y comunicarse con el proceso en el otro extremo. Si la canalización está ocupada, la función de informes esperará hasta que la canalización está disponible o se agote el tiempo de espera. El tiempo de espera puede establecerse mediante el constructor o una llamada a [CDebugReportHook::SetTimeout](#settimeout).  
  
 El código de esta función se ejecuta en el contexto de seguridad subyacente del subproceso que realiza la llamada, es decir, la suplantación está deshabilitada para la duración de esta función.  
  
##  <a name="removehook"></a>CDebugReportHook::RemoveHook  
 Llamar a este método para dejar de enviar informes de depuración a la canalización con nombre y restaurar el enlace de informe anterior.  
  
```
void RemoveHook() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) para restaurar el enlace de informe anterior.  
  
##  <a name="sethook"></a>CDebugReportHook::SetHook  
 Llame a este método para empezar a enviar informes de depuración a la canalización con nombre.  
  
```
void SetHook() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [_CrtSetReportHook2](../../c-runtime-library/reference/crtsetreporthook2-crtsetreporthookw2.md) enruta a través de informes de depuración [CDebugReportHookProc](#cdebugreporthookproc) a la canalización con nombre. Esta clase realiza un seguimiento de lo enlace de informe anterior para que pueda restaurar cuando [RemoveHook](#removehook) se llama.  
  
##  <a name="setpipename"></a>CDebugReportHook::SetPipeName  
 Llame a este método para establecer la máquina y el nombre de la canalización a la que se enviarán informes de depuración.  
  
```
BOOL SetPipeName(
    LPCSTR szMachineName = ".",
    LPCSTR szPipeName = "AtlsDbgPipe") throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `szMachineName`  
 El nombre del equipo al que se debe enviar el resultado de depuración.  
  
 `szPipeName`  
 El nombre de la canalización con nombre al que se debe enviar el resultado de depuración.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve TRUE si se ejecuta correctamente, FALSE en caso de error.  
  
##  <a name="settimeout"></a>CDebugReportHook::SetTimeout  
 Llamar a este método para establecer el tiempo en milisegundos que esperará esta clase para que la canalización con nombre esté disponible.  
  
```
void SetTimeout(DWORD dwTimeout);
```  
  
### <a name="parameters"></a>Parámetros  
 `dwTimeout`  
 El tiempo en milisegundos que esperará esta clase para que la canalización con nombre esté disponible.  
  
## <a name="see-also"></a>Vea también  
 [Clases](../../atl/reference/atl-classes.md)

