---
title: Clase CAtlModuleT | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlModuleT
- ATLBASE/ATL::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::CAtlModuleT
- ATLBASE/ATL::CAtlModuleT::InitLibId
- ATLBASE/ATL::CAtlModuleT::RegisterAppId
- ATLBASE/ATL::CAtlModuleT::RegisterServer
- ATLBASE/ATL::CAtlModuleT::UnregisterAppId
- ATLBASE/ATL::CAtlModuleT::UnregisterServer
- ATLBASE/ATL::CAtlModuleT::UpdateRegistryAppId
dev_langs:
- C++
helpviewer_keywords:
- CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
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
translationtype: Machine Translation
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 9c0c6a2302932df06db7166d83fe9a561dfe38ac
ms.lasthandoff: 02/24/2017

---
# <a name="catlmodulet-class"></a>Clase CAtlModuleT
Esta clase implementa un módulo ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```  
  
#### <a name="parameters"></a>Parámetros  
 `T`  
 La clase derivada de `CAtlModuleT`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlModuleT::InitLibId](#initlibid)|Inicializa al miembro de datos que contiene el GUID del módulo actual.|  
|[CAtlModuleT::RegisterAppId](#registerappid)|Agrega el archivo ejecutable en el registro.|  
|[CAtlModuleT::RegisterServer](#registerserver)|Agrega el servicio en el registro.|  
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Elimina el archivo EXE del registro.|  
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Quita el servicio de registro.|  
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Actualiza la información del archivo EXE en el registro.|  
  
## <a name="remarks"></a>Comentarios  
 `CAtlModuleT`, derivado de [CAtlModule](../../atl/reference/catlmodule-class.md), implemente un archivo ejecutable (EXE) o un módulo ATL de servicio (EXE). Un módulo ejecutable es un servidor local fuera de proceso, mientras que un módulo de servicio es una aplicación de Windows que se ejecuta en segundo plano cuando se inicia Windows.  
  
 `CAtlModuleT`proporciona compatibilidad para inicializar, registrar y anular el registro del módulo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `CAtlModuleT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="catlmodulet"></a>CAtlModuleT::CAtlModuleT  
 El constructor.  
  
```
CAtlModuleT() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Llamadas [CAtlModuleT::InitLibId](#initlibid).  
  
##  <a name="initlibid"></a>CAtlModuleT::InitLibId  
 Inicializa al miembro de datos que contiene el GUID del módulo actual.  
  
```
static void InitLibId() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El constructor llama a [CAtlModuleT::CAtlModuleT](#catlmodulet).  
  
##  <a name="registerappid"></a>CAtlModuleT::RegisterAppId  
 Agrega el archivo ejecutable en el registro.  
  
```
HRESULT RegisterAppId() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="registerserver"></a>CAtlModuleT::RegisterServer  
 Agrega el servicio en el registro.  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegTypeLib`  
 Es TRUE si la biblioteca de tipos se registrará. El valor predeterminado es FALSE.  
  
 `pCLSID`  
 Señala al CLSID del objeto que se va a registrar. Si es NULL (valor predeterminado), todos los objetos del mapa de objetos que se registra.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId  
 Elimina el archivo EXE del registro.  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="unregisterserver"></a>CAtlModuleT::UnregisterServer  
 Quita el servicio de registro.  
  
```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bUnRegTypeLib`  
 Es TRUE si la biblioteca de tipos también se va a anular.  
  
 `pCLSID`  
 Señala el CLSID del objeto que se va a anular. Si es NULL (valor predeterminado), todos los objetos del mapa de objetos no se registra.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
##  <a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId  
 Actualiza la información del archivo EXE en el registro.  
  
```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegister`  
 Reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
## <a name="see-also"></a>Vea también  
 [Clase de CAtlModule](../../atl/reference/catlmodule-class.md)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)

