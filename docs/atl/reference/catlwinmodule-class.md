---
title: Clase CAtlWinModule | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::CAtlWinModule
- ATL.CAtlWinModule
- CAtlWinModule
dev_langs:
- C++
helpviewer_keywords:
- CAtlWinModule class
ms.assetid: 7ec844af-0f68-4a34-b0c8-9de50a025df0
caps.latest.revision: 20
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
ms.sourcegitcommit: 5a0c6a1062330f952bb8fa52bc934f6754465513
ms.openlocfilehash: 6db3ae9e610605524683e984f2aba602b1daf0d4
ms.lasthandoff: 02/24/2017

---
# <a name="catlwinmodule-class"></a>Clase CAtlWinModule
Esta clase proporciona compatibilidad para los componentes de la ventana ATL.  
  
> [!IMPORTANT]
>  Esta clase y sus miembros no pueden utilizarse en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
## <a name="syntax"></a>Sintaxis  
  
```
class CAtlWinModule : public _ATL_WIN_MODULE
```  
  
## <a name="members"></a>Miembros  
  
### <a name="public-constructors"></a>Constructores públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlWinModule::CAtlWinModule](#catlwinmodule)|El constructor.|  
|[CAtlWinModule:: ~ CAtlWinModule](#dtor)|Destructor.|  
  
### <a name="public-methods"></a>Métodos públicos  
  
|Nombre|Descripción|  
|----------|-----------------|  
|[CAtlWinModule::AddCreateWndData](#addcreatewnddata)|Agrega un objeto de datos.|  
|[CAtlWinModule::ExtractCreateWndData](#extractcreatewnddata)|Devuelve un puntero al objeto de datos del módulo de ventana.|  
  
## <a name="remarks"></a>Comentarios  
 Esta clase proporciona compatibilidad para todas las clases ATL que requieren características de la ventana.  
  
## <a name="inheritance-hierarchy"></a>Jerarquía de herencia  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)  
  
 `CAtlWinModule`  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
##  <a name="a-nameaddcreatewnddataa--catlwinmoduleaddcreatewnddata"></a><a name="addcreatewnddata"></a>CAtlWinModule::AddCreateWndData  
 Este método inicializa y agrega un `_AtlCreateWndData` estructura.  
  
```
void AddCreateWndData(_AtlCreateWndData* pData, void* pObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `pData`  
 Puntero a la `_AtlCreateWndData` estructura se inicialicen y se agregará al módulo actual.  
  
 `pObject`  
 Puntero a un objeto **esto** puntero.  
  
### <a name="remarks"></a>Comentarios  
 Este método llama a [AtlWinModuleAddCreateWndData](http://msdn.microsoft.com/library/8463a6ed-07ea-4aad-92ec-ded681601b32) que inicializa un [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) estructura. Esta estructura se almacenará la **esto** puntero, utilizado para obtener la instancia de clase en los procedimientos de ventana.  
  
##  <a name="a-namecatlwinmodulea--catlwinmodulecatlwinmodule"></a><a name="catlwinmodule"></a>CAtlWinModule::CAtlWinModule  
 El constructor.  
  
```
CAtlWinModule();
```  
  
### <a name="remarks"></a>Comentarios  
 Si se produce un error en la inicialización, un **EXCEPTION_NONCONTINUABLE** se produce la excepción.  
  
##  <a name="a-namedtora--catlwinmodulecatlwinmodule"></a><a name="dtor"></a>CAtlWinModule:: ~ CAtlWinModule  
 Destructor.  
  
```
~CAtlWinModule();
```  
  
### <a name="remarks"></a>Comentarios  
 Libera todos los recursos asignados.  
  
##  <a name="a-nameextractcreatewnddataa--catlwinmoduleextractcreatewnddata"></a><a name="extractcreatewnddata"></a>CAtlWinModule::ExtractCreateWndData  
 Este método devuelve un puntero a un `_AtlCreateWndData` estructura.  
  
```
void* ExtractCreateWndData();
```  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la `_AtlCreateWndData` estructura agregado previamente con [CAtlWinModule::AddCreateWndData](#addcreatewnddata), o NULL si no hay ningún objeto está disponible.  
  
## <a name="see-also"></a>Vea también  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module)   
 [Información general de la clase](../../atl/atl-class-overview.md)   
 [Clases de módulo](../../atl/atl-module-classes.md)

