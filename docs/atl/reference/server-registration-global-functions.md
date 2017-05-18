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
dev_langs:
- C++
ms.assetid: c2f0a35d-857c-4538-a44d-c4ea0db63b06
caps.latest.revision: 19
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 4ace3bb50d824827071260e3f43cec3cda32742f
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="server-registration-global-functions"></a>Funciones globales de registro de servidor
Estas funciones proporcionan compatibilidad para registrar y anular el registro de objetos de servidor en el mapa de objetos.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlComModuleRegisterServer](#atlcommoduleregisterserver)|Esta función se invoca para registrar todos los objetos del mapa de objetos.|  
|[AtlComModuleUnregisterServer](#atlcommoduleunregisterserver)|Esta función se invoca para anular el registro de todos los objetos del mapa de objetos.|  
|[AtlComModuleRegisterClassObjects](#atlcommoduleregisterclassobjects)|Esta función se invoca para registrar los objetos de clase.|  
|[AtlComModuleRevokeClassObjects](#atlcommodulerevokeclassobjects)|Esta función se invoca para revocar los objetos de clase desde un módulo COM.|  
|[AtlComModuleGetClassObject](#atlcommodulegetclassobject)|Esta función se llama para obtener el objeto de clase.|  

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
 Es TRUE si la biblioteca de tipos se registrará.  
  
 `pCLSID`  
 Señala al CLSID del objeto que se va a registrar. Si es NULL, se registrarán todos los objetos del mapa de objetos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 `AtlComModuleRegisterServer`recorre el mapa de objetos ATL generado automáticamente y registra cada objeto en el mapa. Si `pCLSID` no es NULL, entonces sólo en el objeto al que hace referencia `pCLSID` está registrada; de lo contrario, todos los objetos están registrados.  
  
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
 Es TRUE si la biblioteca de tipos se registrará.  
  
 `pCLSID`  
 Señala el CLSID del objeto que se va a anular. Si es NULL, todos los objetos del mapa de objetos será sin registrar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 `AtlComModuleUnregisterServer`recorre el mapa de objetos ATL y anula el registro de cada objeto en el mapa. Si `pCLSID` no es NULL, entonces sólo en el objeto al que hace referencia `pCLSID` está registrada; en caso contrario, todos los objetos que están registrados.  
  
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
 Especifica el contexto en el que se ejecutará el objeto de clase. Los valores posibles son CLSCTX_INPROC_SERVER, CLSCTX_INPROC_HANDLER o CLSCTX_LOCAL_SERVER. Consulte [CLSCTX](http://msdn.microsoft.com/library/windows/desktop/ms693716) para obtener más detalles.  
  
 `dwFlags`  
 Determina los tipos de conexión para el objeto de clase. Los valores posibles son REGCLS_SINGLEUSE, REGCLS_MULTIPLEUSE o REGCLS_MULTI_SEPARATE. Consulte [REGCLS](http://msdn.microsoft.com/library/windows/desktop/ms679697) para obtener más detalles.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza esta función auxiliar [CComModule::RegisterClassObjects](ccommodule-class.md#registerclassobjects) (obsoleto en ATL 7.0) y [CAtlExeModuleT::RegisterClassObjects](catlexemodulet-class.md#registerclassobjects).  
  
##  <a name="atlcommodulerevokeclassobjects"></a>AtlComModuleRevokeClassObjects  
 Esta función se invoca para quitar el generador o generadores de clases de la tabla de objetos en ejecución.  
  
```
ATLINLINE ATLAPI AtlComModuleRevokeClassObjects(_ATL_COM_MODULE* pComModule);
```  
  
### <a name="parameters"></a>Parámetros  
 `pComModule`  
 Puntero al módulo COM.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza esta función auxiliar [CComModule::RevokeClassObjects](ccommodule-class.md#revokeclassobjects) (obsoleto en ATL 7.0) y [CAtlExeModuleT::RevokeClassObjects](catlexemodulet-class.md#revokeclassobjects).  
  
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
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Se utiliza esta función auxiliar [CComModule::GetClassObject](ccommodule-class.md#getclassobject) (obsoleto en ATL 7.0) y [CAtlDllModuleT::GetClassObject](catldllmodulet-class.md#getclassobject).  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)

