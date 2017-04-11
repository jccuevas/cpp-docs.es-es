---
title: Clase CAtlComModule | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlComModule
- ATLBASE/ATL::CAtlComModule
- ATLBASE/ATL::CAtlComModule::CAtlComModule
- ATLBASE/ATL::CAtlComModule::RegisterServer
- ATLBASE/ATL::CAtlComModule::RegisterTypeLib
- ATLBASE/ATL::CAtlComModule::UnregisterServer
- ATLBASE/ATL::CAtlComModule::UnRegisterTypeLib
dev_langs:
- C++
helpviewer_keywords:
- CAtlComModule class
ms.assetid: af5dd71a-a0d1-4a2e-9a24-154a03381c75
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
ms.sourcegitcommit: d2d39abf526a58b8442107b5ee816f316ae841f5
ms.openlocfilehash: 02381d00226f40c5c84b2d957dfee6881742febb
ms.lasthandoff: 03/31/2017

---
# <a name="catlcommodule-class"></a>Clase CAtlComModule
Esta clase implementa un módulo de servidor COM.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlComModule : public _ATL_COM_MODULE
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlComModule::CAtlComModule](#catlcommodule)|El constructor.|  
|[CAtlComModule:: ~ CAtlComModule](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlComModule::RegisterServer](#registerserver)|Llamar a este método para actualizar el registro del sistema para cada objeto del mapa de objetos.|  
|[CAtlComModule::RegisterTypeLib](#registertypelib)|Llamar a este método para registrar una biblioteca de tipos.|  
|[CAtlComModule::UnregisterServer](#unregisterserver)|Llame a este método para anular el registro de cada objeto del mapa de objetos.|  
|[CAtlComModule::UnRegisterTypeLib](#unregistertypelib)|Llame a este método para anular el registro de una biblioteca de tipos.|  
  
## <a name="remarks"></a>Comentarios  
 `CAtlComModule`implementa un módulo de servidor COM, lo que permite un cliente tener acceso a los componentes del módulo.  
  
 Esta clase reemplaza el atributo obsolete [CComModule](../../atl/reference/ccommodule-class.md) clase usada en versiones anteriores de ATL. Vea [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)  
  
 `CAtlComModule`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="catlcommodule"></a>CAtlComModule::CAtlComModule  
 El constructor.  
  
```
CAtlComModule() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Inicializa el módulo.  
  
##  <a name="dtor"></a>CAtlComModule:: ~ CAtlComModule  
 Destructor.  
  
```
~CAtlComModule();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los generadores de clases.  
  
##  <a name="registerserver"></a>CAtlComModule::RegisterServer  
 Llamar a este método para actualizar el registro del sistema para cada objeto del mapa de objetos.  
  
```
HRESULT RegisterServer(BOOL bRegTypeLib = FALSE, const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegTypeLib`  
 TRUE si la biblioteca de tipos se registrará. El valor predeterminado es FALSE.  
  
 `pCLSID`  
 Señala al CLSID del objeto que se va a registrar. Si se registrará NULL (valor predeterminado), todos los objetos del mapa de objetos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llama a la función global [AtlComModuleRegisterServer](server-registration-global-functions.md#atlcommoduleregisterserver).  
  
##  <a name="registertypelib"></a>CAtlComModule::RegisterTypeLib  
 Llamar a este método para registrar una biblioteca de tipos.  
  
```
HRESULT RegisterTypeLib(LPCTSTR lpszIndex);
HRESULT RegisterTypeLib();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszIndex`  
 Cadena con el formato "\\\N", donde N es el índice de entero del recurso de biblioteca de tipos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Agrega información sobre una biblioteca de tipos para el registro del sistema. Si la instancia del módulo que contiene varias bibliotecas de tipos, utilice la primera versión de este método para especificar qué biblioteca de tipos se debe usar.  
  
##  <a name="unregisterserver"></a>CAtlComModule::UnregisterServer  
 Llame a este método para anular el registro de cada objeto del mapa de objetos.  
  
```
HRESULT UnregisterServer(
  BOOL bRegTypeLib = FALSE,  
  const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegTypeLib`  
 TRUE si la biblioteca de tipos se puede anular el registro. El valor predeterminado es FALSE.  
  
 `pCLSID`  
 Señala el CLSID del objeto que se puede anular el registro. Si es NULL (valor predeterminado), todos los objetos del mapa de objetos se cancelará.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llama a la función global [AtlComModuleUnregisterServer](server-registration-global-functions.md#atlcommoduleunregisterserver).  
  
##  <a name="unregistertypelib"></a>CAtlComModule::UnRegisterTypeLib  
 Llame a este método para anular el registro de una biblioteca de tipos.  
  
```
HRESULT UnRegisterTypeLib(LPCTSTR lpszIndex);
HRESULT UnRegisterTypeLib();
```  
  
### <a name="parameters"></a>Parámetros  
 `lpszIndex`  
 Cadena con el formato "\\\N", donde N es el índice de entero del recurso de biblioteca de tipos.  
  
### <a name="remarks"></a>Comentarios  
 Quita la información acerca de una biblioteca de tipos desde el registro del sistema. Si la instancia del módulo que contiene varias bibliotecas de tipos, utilice la primera versión de este método para especificar qué biblioteca de tipos se debe usar.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK si se ejecuta correctamente, o un valor HRESULT de error en caso de error.  
  
## <a name="see-also"></a>Vea también  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)   
 [Información general de clases](../../atl/atl-class-overview.md)

