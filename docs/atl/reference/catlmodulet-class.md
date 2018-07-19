---
title: CAtlModuleT (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1dd5bd4c7bc88d0a0acc8abc18b0d7b3462b7f52
ms.sourcegitcommit: 7d68f8303e021e27dc8f4d36e764ed836e93d24f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/06/2018
ms.locfileid: "37880851"
---
# <a name="catlmodulet-class"></a>CAtlModuleT (clase)
Esta clase implementa un módulo de ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
template <class T>  
class ATL_NO_VTABLE CAtlModuleT : public CAtlModule
```  
  
#### <a name="parameters"></a>Parámetros  
 *T*  
 La clase derivada de `CAtlModuleT`.  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModuleT::CAtlModuleT](#catlmodulet)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CAtlModuleT::InitLibId](#initlibid)|Inicializa al miembro de datos que contiene el GUID del módulo actual.|  
|[CAtlModuleT::RegisterAppId](#registerappid)|Agrega el archivo EXE en el registro.|  
|[CAtlModuleT::RegisterServer](#registerserver)|Agrega el servicio en el registro.|  
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Quita el archivo EXE del registro.|  
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Quita el servicio del registro.|  
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Actualiza la información del archivo EXE en el registro.|  
  
## <a name="remarks"></a>Comentarios  
 `CAtlModuleT`, derivado de [CAtlModule](../../atl/reference/catlmodule-class.md), implemente un archivo ejecutable (EXE) o un módulo ATL de servicio (EXE). Un módulo ejecutable es un servidor local fuera de proceso, mientras que un módulo de servicio es una aplicación de Windows que se ejecuta en segundo plano cuando se inicia Windows.  
  
 `CAtlModuleT` proporciona compatibilidad para inicializar, registrar y anular el registro del módulo.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_MODULE](atl-typedefs.md#_atl_module)  

  
 [CAtlModule](../../atl/reference/catlmodule-class.md)  
  
 `CAtlModuleT`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="catlmodulet"></a>  CAtlModuleT::CAtlModuleT  
 El constructor.  
  
```
CAtlModuleT() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Las llamadas [CAtlModuleT::InitLibId](#initlibid).  
  
##  <a name="initlibid"></a>  CAtlModuleT::InitLibId  
 Inicializa al miembro de datos que contiene el GUID del módulo actual.  
  
```
static void InitLibId() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 El constructor llama a [CAtlModuleT::CAtlModuleT](#catlmodulet).  
  
##  <a name="registerappid"></a>  CAtlModuleT::RegisterAppId  
 Agrega el archivo EXE en el registro.  
  
```
HRESULT RegisterAppId() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
##  <a name="registerserver"></a>  CAtlModuleT::RegisterServer  
 Agrega el servicio en el registro.  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *bRegTypeLib*  
 TRUE si la biblioteca de tipos es que se registrarán. El valor predeterminado es FALSE.  
  
 *pTypeInfo*  
 Señala el CLSID del objeto que se registrarán. Si es NULL (valor predeterminado), todos los objetos en el mapa de objetos que se registra.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
##  <a name="unregisterappid"></a>  CAtlModuleT::UnregisterAppId  
 Quita el archivo EXE del registro.  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
##  <a name="unregisterserver"></a>  CAtlModuleT::UnregisterServer  
 Quita el servicio del registro.  
  
```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *bUnRegTypeLib*  
 TRUE si la biblioteca de tipos también se va a anular el registro.  
  
 *pTypeInfo*  
 Señala el CLSID del objeto que se va a anular. Si es NULL (valor predeterminado), todos los objetos en el mapa de objetos se anulará.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
##  <a name="updateregistryappid"></a>  CAtlModuleT::UpdateRegistryAppId  
 Actualiza la información del archivo EXE en el registro.  
  
```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *bInscríbase al*  
 Reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un error HRESULT en caso de error.  
  
## <a name="see-also"></a>Vea también  
 [CAtlModule (clase)](../../atl/reference/catlmodule-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)
