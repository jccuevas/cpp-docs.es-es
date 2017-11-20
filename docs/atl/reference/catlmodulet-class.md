---
title: Clase CAtlModuleT | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
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
dev_langs: C++
helpviewer_keywords: CAtlModuleT class
ms.assetid: 9b74d02f-9117-47b1-a05e-c5945f83dd2b
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: e336b7c9ed868e4aa1538c6673371b33123a4072
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
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
|[CAtlModuleT::RegisterAppId](#registerappid)|Agrega el archivo EXE en el registro.|  
|[CAtlModuleT::RegisterServer](#registerserver)|Agrega el servicio en el registro.|  
|[CAtlModuleT::UnregisterAppId](#unregisterappid)|Elimina el archivo EXE del registro.|  
|[CAtlModuleT::UnregisterServer](#unregisterserver)|Elimina el servicio del registro.|  
|[CAtlModuleT::UpdateRegistryAppId](#updateregistryappid)|Actualiza la información de archivo EXE en el registro.|  
  
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
 Llamado por el constructor [CAtlModuleT::CAtlModuleT](#catlmodulet).  
  
##  <a name="registerappid"></a>CAtlModuleT::RegisterAppId  
 Agrega el archivo EXE en el registro.  
  
```
HRESULT RegisterAppId() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="registerserver"></a>CAtlModuleT::RegisterServer  
 Agrega el servicio en el registro.  
  
```
HRESULT RegisterServer(
    BOOL bRegTypeLib = FALSE,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegTypeLib`  
 TRUE si la biblioteca de tipos se registrará. El valor predeterminado es FALSE.  
  
 `pCLSID`  
 Señala al CLSID del objeto que se va a registrar. Si se registrará NULL (valor predeterminado), todos los objetos del mapa de objetos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="unregisterappid"></a>CAtlModuleT::UnregisterAppId  
 Elimina el archivo EXE del registro.  
  
```
HRESULT UnregisterAppId() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="unregisterserver"></a>CAtlModuleT::UnregisterServer  
 Elimina el servicio del registro.  
  
```
HRESULT UnregisterServer(
    BOOL bUnRegTypeLib,
    const CLSID* pCLSID = NULL) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bUnRegTypeLib`  
 Es TRUE si la biblioteca de tipos es también se va a anular.  
  
 `pCLSID`  
 Señala el CLSID del objeto que se puede anular el registro. Si es NULL (valor predeterminado), todos los objetos del mapa de objetos se cancelará.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
##  <a name="updateregistryappid"></a>CAtlModuleT::UpdateRegistryAppId  
 Actualiza la información de archivo EXE en el registro.  
  
```
static HRESULT WINAPI UpdateRegistryAppId(BOOL /* bRegister*/) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegister`  
 Reservado.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
## <a name="see-also"></a>Vea también  
 [Clase de CAtlModule](../../atl/reference/catlmodule-class.md)   
 [Información general de clases](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)
