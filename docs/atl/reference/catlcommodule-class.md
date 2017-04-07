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
ms.sourcegitcommit: 604a4bf49490ad2599c857eb3afd527d67e1e25b
ms.openlocfilehash: 6b933b5388fccc2dc0e31d035aa7eb56de3b1866
ms.lasthandoff: 02/24/2017

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
 `CAtlComModule`implementa un módulo de servidor COM, lo que permite a los componentes del módulo de acceso a un cliente.  
  
 Esta clase reemplaza la obsoleta [CComModule](../../atl/reference/ccommodule-class.md) clase utilizada en versiones anteriores de ATL. Consulte [clases de módulo ATL](../../atl/atl-module-classes.md) para obtener más detalles.  
  
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
 Es TRUE si la biblioteca de tipos se registrará. El valor predeterminado es FALSE.  
  
 `pCLSID`  
 Señala al CLSID del objeto que se va a registrar. Si es NULL (valor predeterminado), todos los objetos del mapa de objetos que se registra.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llama a la función global [AtlComModuleRegisterServer](http://msdn.microsoft.com/library/d11a0c91-0c56-4b1b-a5f5-1287970f798b).  
  
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
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Agrega información sobre una biblioteca de tipos para el registro del sistema. Si la instancia del módulo que contiene varias bibliotecas de tipos, utilice la primera versión de este método para especificar que se debe utilizar la biblioteca de tipos.  
  
##  <a name="unregisterserver"></a>CAtlComModule::UnregisterServer  
 Llame a este método para anular el registro de cada objeto del mapa de objetos.  
  
```
HRESULT UnregisterServer(
  BOOL bRegTypeLib = FALSE,  
  const CLSID* pCLSID = NULL);
```  
  
### <a name="parameters"></a>Parámetros  
 `bRegTypeLib`  
 Es TRUE si se va a anular la biblioteca de tipos. El valor predeterminado es FALSE.  
  
 `pCLSID`  
 Señala el CLSID del objeto que se va a anular. Si es NULL (valor predeterminado), todos los objetos del mapa de objetos no se registra.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
### <a name="remarks"></a>Comentarios  
 Llama a la función global [AtlComModuleUnregisterServer](http://msdn.microsoft.com/library/c4ef3da4-def7-4aaf-b005-573a02e389d5).  
  
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
 Quita la información acerca de una biblioteca de tipos del registro del sistema. Si la instancia del módulo que contiene varias bibliotecas de tipos, utilice la primera versión de este método para especificar que se debe utilizar la biblioteca de tipos.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve S_OK en caso de éxito o error HRESULT en caso de error.  
  
## <a name="see-also"></a>Vea también  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module)   
 [Información general de la clase](../../atl/atl-class-overview.md)

