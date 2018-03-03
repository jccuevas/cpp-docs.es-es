---
title: Funciones globales de registro de servidor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlComModuleRegisterServer
- atlbase/ATL::AtlComModuleUnregisterServer
- atlbase/ATL::AtlComModuleRegisterClassObjects
- atlbase/ATL::AtlComModuleRevokeClassObjects
- atlbase/ATL::AtlComModuleGetClassObject
dev_langs:
- C++
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 0f5cfffbcc47555ee8cff7cd6e18ea54b5524607
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="server-registration-global-functions"></a>Funciones globales de registro de servidor
Estas funciones proporcionan compatibilidad para registrar y anular el registro de los objetos de servidor en el mapa de objetos.  
  
> [!IMPORTANT]
>  Las funciones se enumeran en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
|||  
|-|-|  
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Esta función se invoca para registrar todos los objetos del mapa de objetos.|  
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Esta función se invoca para anular el registro de todos los objetos del mapa de objetos.|  
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Esta función se invoca para registrar los objetos de clase.|  
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Esta función se invoca para revocar los objetos de clase de un módulo COM.|  
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Se llama a esta función para obtener el objeto de clase.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
   
##  <a name="atlcommoduleregisterserver"></a>AtlComModuleRegisterServer  
 Esta función se invoca para registrar todos los objetos del mapa de objetos.  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>Parámetros  
 `pComModule`  
 Puntero al módulo COM.  
  
 `bRegTypeLib`  
 TRUE si la biblioteca de tipos se registrará.  
  
 `pCLSID`  
 Señala al CLSID del objeto que se va a registrar. Si es NULL, se registrará todos los objetos del mapa de objetos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 `AtlComModuleRegisterServer`recorre el mapa de objetos ATL generado automáticamente y registra cada objeto en el mapa. Si `pCLSID` no es NULL y, a continuación, solo el objeto al que hace referencia `pCLSID` está registrado; en caso contrario, todos los objetos están registrados.  
  
 Esta función se invoca [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver).  
  
##  <a name="atlcommoduleunregisterserver"></a>AtlComModuleUnregisterServer  
 Esta función se invoca para anular el registro de todos los objetos del mapa de objetos.  
  
```
ATLINLINE ATLAPI AtlComModuleUnregisterServer(
    _ATL_COM_MODULE* pComModule,
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID);
```  
  
### <a name="parameters"></a>Parámetros  
 `pComModule`  
 Puntero al módulo COM.  
  
 `bUnRegTypeLib`  
 TRUE si la biblioteca de tipos se registrará.  
  
 `pCLSID`  
 Señala el CLSID del objeto que se puede anular el registro. Si es NULL se cancelará todos los objetos del mapa de objetos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 `AtlComModuleUnregisterServer`recorre el mapa de objetos ATL y anula el registro de cada objeto en el mapa. Si `pCLSID` no es NULL y, a continuación, solo el objeto al que hace referencia `pCLSID` está registrada; de lo contrario todos los objetos se eliminan del registrados.  
  
 Esta función se invoca [CAtlComModule::UnregisterServer](catlcommodule-class.md#unregisterserver).  
  
##  <a name="atlcommoduleregisterclassobjects"></a>AtlComModuleRegisterClassObjects  
 Esta función se invoca para registrar los objetos de clase.  
  
```
ATLINLINE ATLAPI AtlComModuleRegisterClassObjects(
    _ATL_COM_MODULE* pComModule,
    DWORD dwClsContext,
    DWORD dwFlags);
```  
  
### <a name="parameters"></a>Parámetros  
 `pComModule`  
 Puntero al módulo COM.  
  
 `dwClsContext`  
 Especifica el contexto en el que se ejecutará el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER. Vea [CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716) para obtener más detalles.  
  
 `dwFlags`  
 Determina los tipos de conexión para el objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE. Vea [REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697) para obtener más detalles.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función auxiliar es usada por [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (obsoleta en ATL 7.0) y [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).  
  
##  <a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects  
 Esta función se invoca para quitar el generador o generadores de clases de la tabla de objetos en ejecución.  
  
```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```  
  
### <a name="parameters"></a>Parámetros  
 `pComModule`  
 Puntero al módulo COM.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función auxiliar es usada por [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (obsoleta en ATL 7.0) y [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).  
  
##  <a name="atlcommodulegetclassobject"></a>AtlComModuleGetClassObject  
 Esta función se invoca para devolver el generador de clases.  
  
```
ATLINLINE ATLAPI AtlComModuleGetClassObject(
    _ATL_COM_MODULE* pComModule,
    REFCLSID rclsid,
    REFIID riid,
    LPVOID* ppv);
```  
  
### <a name="parameters"></a>Parámetros  
 `pComModule`  
 Puntero al módulo COM.  
  
 `rclsid`  
 El CLSID del objeto que se va a crear.  
  
 `riid`  
 El IID de la interfaz solicitada.  
  
 `ppv`  
 Un puntero al puntero de interfaz identificado por `riid`. Si el objeto no admite esta interfaz, `ppv` se establece en NULL.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Esta función auxiliar es usada por [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (obsoleta en ATL 7.0) y [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)
