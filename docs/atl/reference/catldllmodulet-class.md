---
title: Clase CAtlDllModuleT | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::CAtlDllModuleT
- ATLBASE/ATL::CAtlDllModuleT::DllCanUnloadNow
- ATLBASE/ATL::CAtlDllModuleT::DllGetClassObject
- ATLBASE/ATL::CAtlDllModuleT::DllMain
- ATLBASE/ATL::CAtlDllModuleT::DllRegisterServer
- ATLBASE/ATL::CAtlDllModuleT::DllUnregisterServer
- ATLBASE/ATL::CAtlDllModuleT::GetClassObject
dev_langs: C++
helpviewer_keywords: CAtlDllModuleT class
ms.assetid: 351d5767-8257-4878-94be-45a85e31a72d
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 650924898532e352df30d7e8173620b974f30138
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="catldllmodulet-class"></a>Clase CAtlDllModuleT
Esta clase representa el módulo para un archivo DLL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlDllModuleT : public CAtlModuleT<T>
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `CAtlDllModuleT`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlDllModuleT::CAtlDllModuleT](#catldllmodulet)|El constructor.|  
|[CAtlDllModuleT:: ~ CAtlDllModuleT](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlDllModuleT::DllCanUnloadNow](#dllcanunloadnow)|Comprueba si se puede descargar el archivo DLL.|  
|[CAtlDllModuleT::DllGetClassObject](#dllgetclassobject)|Devuelve un generador de clases.|  
|[CAtlDllModuleT::DllMain](#dllmain)|El punto de entrada opcional en una biblioteca de vínculos dinámicos (DLL).|  
|[CAtlDllModuleT::DllRegisterServer](#dllregisterserver)|Agrega entradas al registro del sistema para los objetos en el archivo DLL.|  
|[CAtlDllModuleT::DllUnregisterServer](#dllunregisterserver)|Quita las entradas del registro del sistema para los objetos en el archivo DLL.|  
|[CAtlDllModuleT::GetClassObject](#getclassobject)|Devuelve un generador de clases. Invocado por [DllGetClassObject](#dllgetclassobject).|  
  
## <a name="remarks"></a>Comentarios  
 `CAtlDllModuleT`representa el módulo de una biblioteca de vínculos dinámicos (DLL) y proporciona funciones que se usan en todos los proyectos DLL. Esta especialización de [CAtlModuleT](../../atl/reference/catlmodulet-class.md) clase incluye compatibilidad para el registro.  
  
 Para obtener más información sobre los módulos de ATL, vea [clases de módulo ATL](../../atl/atl-module-classes.md).  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  
  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 [CAtlModuleT](../../atl/reference/catlmodulet-class.md)  
  
 `CAtlDllModuleT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="catldllmodulet"></a>CAtlDllModuleT::CAtlDllModuleT  
 El constructor.  
  
```
CAtlDllModuleT() throw();
```  
  
##  <a name="dtor"></a>CAtlDllModuleT:: ~ CAtlDllModuleT  
 Destructor.  
  
```
~CAtlDllModuleT() throw();
```  
  
##  <a name="dllcanunloadnow"></a>CAtlDllModuleT::DllCanUnloadNow  
 Comprueba si se puede descargar el archivo DLL.  
  
```
HRESULT DllCanUnloadNow() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se puede descargar el archivo DLL o S_FALSE si no es posible.  
  
##  <a name="dllgetclassobject"></a>CAtlDllModuleT::DllGetClassObject  
 Devuelve el generador de clases.  
  
```
HRESULT DllGetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `rclsid`  
 El CLSID del objeto que se va a crear.  
  
 `riid`  
 El IID de la interfaz solicitada.  
  
 `ppv`  
 Un puntero al puntero de interfaz identificado por `riid`. Si el objeto no admite esta interfaz, `ppv` se establece en NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="dllmain"></a>CAtlDllModuleT::DllMain  
 El punto de entrada opcional en una biblioteca de vínculos dinámicos (DLL).  
  
```
BOOL WINAPI DllMain(DWORD dwReason, LPVOID /* lpReserved*/) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `dwReason`  
 Si el conjunto de llamadas de notificación DLL_PROCESS_ATTACH, DLL_THREAD_ATTACH y DLL_THREAD_DETACH está deshabilitado.  
  
 *lpReserved*  
 Reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 Siempre devuelve TRUE.  
  
### <a name="remarks"></a>Comentarios  
 Deshabilitar el DLL_THREAD_ATTACH y DLL_THREAD_DETACH notificación llamadas pueden ser una optimización útil para aplicaciones multiproceso que tiene muchos archivos DLL, que crear y eliminar subprocesos con frecuencia y cuyo archivos DLL no necesita estas notificaciones de nivel de subproceso de datos adjuntos/desasociación.  
  
##  <a name="dllregisterserver"></a>CAtlDllModuleT::DllRegisterServer  
 Agrega entradas al registro del sistema para los objetos en el archivo DLL.  
  
```
HRESULT DllRegisterServer(BOOL bRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegTypeLib`  
 TRUE si la biblioteca de tipos se registrará. El valor predeterminado es TRUE.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="dllunregisterserver"></a>CAtlDllModuleT::DllUnregisterServer  
 Quita las entradas del registro del sistema para los objetos en el archivo DLL.  
  
```
HRESULT DllUnregisterServer(BOOL bUnRegTypeLib = TRUE) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bUnRegTypeLib`  
 Es TRUE si se quita del registro la biblioteca de tipos. El valor predeterminado es TRUE.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="getclassobject"></a>CAtlDllModuleT::GetClassObject  
 Crea un objeto del CLSID especificado.  
  
```
HRESULT GetClassObject(
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `rclsid`  
 El CLSID del objeto que se va a crear.  
  
 `riid`  
 El IID de la interfaz solicitada.  
  
 `ppv`  
 Un puntero al puntero de interfaz identificado por `riid`. Si el objeto no admite esta interfaz, `ppv` se establece en NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Este método es invocado por [CAtlDllModuleT::DllGetClassObject](#dllgetclassobject) y se incluye por compatibilidad con versiones anteriores.  
  
## <a name="see-also"></a>Vea también  
 [Clase CAtlModuleT](../../atl/reference/catlmodulet-class.md)   
 [Clase de CAtlExeModuleT](../../atl/reference/catlexemodulet-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)
