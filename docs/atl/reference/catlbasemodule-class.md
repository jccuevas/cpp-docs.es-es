---
title: Clase CAtlBaseModule | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::CAtlBaseModule
- ATLCORE/ATL::CAtlBaseModule::AddResourceInstance
- ATLCORE/ATL::CAtlBaseModule::GetHInstanceAt
- ATLCORE/ATL::CAtlBaseModule::GetModuleInstance
- ATLCORE/ATL::CAtlBaseModule::GetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::RemoveResourceInstance
- ATLCORE/ATL::CAtlBaseModule::SetResourceInstance
- ATLCORE/ATL::CAtlBaseModule::m_bInitFailed
dev_langs:
- C++
helpviewer_keywords:
- CAtlBaseModule class
ms.assetid: 55ade80c-9b0c-4c51-933e-2158436c1096
caps.latest.revision: 18
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
ms.sourcegitcommit: 0e0c08ddc57d437c51872b5186ae3fc983bb0199
ms.openlocfilehash: 4897f6cf7e12a18401720ad663c90491bb0e599d
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="catlbasemodule-class"></a>Clase CAtlBaseModule
Esta clase se crean instancias en todos los proyectos ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlBaseModule : public _ATL_BASE_MODULE
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlBaseModule::CAtlBaseModule](#catlbasemodule)|El constructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlBaseModule::AddResourceInstance](#addresourceinstance)|Agrega una instancia del recurso a la lista de identificadores almacenados.|  
|[CAtlBaseModule::GetHInstanceAt](#gethinstanceat)|Devuelve un identificador para una instancia del recurso especificado.|  
|[CAtlBaseModule::GetModuleInstance](#getmoduleinstance)|Devuelve la instancia de módulo desde un `CAtlBaseModule` objeto.|  
|[CAtlBaseModule::GetResourceInstance](#getresourceinstance)|Devuelve la instancia de recurso de un `CAtlBaseModule` objeto.|  
|[CAtlBaseModule::RemoveResourceInstance](#removeresourceinstance)|Quita una instancia de recurso de la lista de identificadores almacenados.|  
|[CAtlBaseModule::SetResourceInstance](#setresourceinstance)|Establece la instancia de recurso de un `CAtlBaseModule` objeto.|  
  
### <a name="public-data-members"></a>Miembros de datos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlBaseModule::m_bInitFailed](#m_binitfailed)|Una variable que indica si ha fallado la inicialización del módulo.|  
  
## <a name="remarks"></a>Comentarios  
 Una instancia de `CAtlBaseModule` _AtlBaseModule con nombre está presente en todos los proyectos ATL, que contiene un identificador de la instancia del módulo, un identificador para el módulo que contiene los recursos (que de forma predeterminada, son la misma) y una matriz de identificadores de módulos para proporcionar recursos primarios. `CAtlBaseModule`puede tener acceso con seguridad desde varios subprocesos.  
  
 Esta clase reemplaza la obsoleta [CComModule](../../atl/reference/ccommodule-class.md) clase utilizada en versiones anteriores de ATL.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module)  
  
 `CAtlBaseModule`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
##  <a name="addresourceinstance"></a>CAtlBaseModule::AddResourceInstance  
 Agrega una instancia del recurso a la lista de identificadores almacenados.  
  
```
bool AddResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hInst`  
 Para agregar la instancia de recurso.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si el recurso correctamente se agregó, false en caso contrario.  
  
##  <a name="catlbasemodule"></a>CAtlBaseModule::CAtlBaseModule  
 El constructor.  
  
```
CAtlBaseModule() throw();
```  
  
### <a name="remarks"></a>Comentarios  
 Crea la clase `CAtlBaseModule`.  
  
##  <a name="gethinstanceat"></a>CAtlBaseModule::GetHInstanceAt  
 Devuelve un identificador para una instancia del recurso especificado.  
  
```
HINSTANCE GetHInstanceAt(int i) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 *i*  
 El número de la instancia del recurso.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve el identificador para la instancia de recurso, o NULL si no existe ninguna instancia de recurso correspondiente.  
  
##  <a name="getmoduleinstance"></a>CAtlBaseModule::GetModuleInstance  
 Devuelve la instancia de módulo desde un `CAtlBaseModule` objeto.  
  
```
HINSTANCE GetModuleInstance() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la instancia del módulo.  
  
##  <a name="getresourceinstance"></a>CAtlBaseModule::GetResourceInstance  
 Devuelve la instancia del recurso.  
  
```
HINSTANCE GetResourceInstance() throw();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la instancia del recurso.  
  
##  <a name="m_binitfailed"></a>CAtlBaseModule::m_bInitFailed  
 Una variable que indica si ha fallado la inicialización del módulo.  
  
```
static bool m_bInitFailed;
```  
  
### <a name="remarks"></a>Comentarios  
 True si el módulo inicializa, false si no se pudo inicializar.  
  
##  <a name="removeresourceinstance"></a>CAtlBaseModule::RemoveResourceInstance  
 Quita una instancia de recurso de la lista de identificadores almacenados.  
  
```
bool RemoveResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hInst`  
 Para quitar la instancia de recurso.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve true si se ha quitado correctamente el recurso.  
  
##  <a name="setresourceinstance"></a>CAtlBaseModule::SetResourceInstance  
 Establece la instancia de recurso de un `CAtlBaseModule` objeto.  
  
```
HINSTANCE SetResourceInstance(HINSTANCE hInst) throw();
```  
  
### <a name="parameters"></a>Parámetros  
 `hInst`  
 La nueva instancia del recurso.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve la instancia de recurso actualizado.  
  
## <a name="see-also"></a>Vea también  
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)

