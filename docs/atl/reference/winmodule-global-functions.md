---
title: Funciones globales de WinModule | Documentos de Microsoft
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
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
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
ms.openlocfilehash: c477f4500bd4fe78f21f04c58b02d1b493f72c01
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="winmodule-global-functions"></a>Funciones globales de WinModule
Estas funciones proporcionan compatibilidad para `_AtlCreateWndData` estructurar las operaciones.  
  
> [!IMPORTANT]
>  Las funciones enumeradas en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el [!INCLUDE[wrt](../../atl/reference/includes/wrt_md.md)].  
  
|||  
|-|-|  
|[AtlWinModuleAddCreateWndData](#atlwinmoduleaddcreatewnddata)|Esta función se utiliza para inicializar y agregar una estructura `_AtlCreateWndData`.|  
|[AtlWinModuleExtractCreateWndData](#atlwinmoduleextractcreatewnddata)|Llame a esta función para extraer una estructura `_AtlCreateWndData` existente.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  `            
##  <a name="atlwinmoduleaddcreatewnddata"></a>AtlWinModuleAddCreateWndData  
 Esta función se utiliza para inicializar y agregar una estructura `_AtlCreateWndData`.  
   
```
ATLINLINE ATLAPI_(void) AtlWinModuleAddCreateWndData(
    _ATL_WIN_MODULE* pWinModule,
    _AtlCreateWndData* pData,
    void* pObject);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWinModule`  
 Puntero a un módulo [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) estructura.  
  
 `pData`  
 Puntero a la [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) estructura se inicialicen y se agregará al módulo actual.  
  
 `pObject`  
 Puntero a un objeto **esto** puntero.  
  
### <a name="remarks"></a>Comentarios  
 Inicializa un `_AtlCreateWndData` estructura, que se utiliza para almacenar el **esto** puntero usado para hacer referencia a instancias de clase y lo agrega a la lista que hace referencia a un módulo `_ATL_WIN_MODULE70` estructura. Llama a [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).  
  
##  <a name="atlwinmoduleextractcreatewnddata"></a>AtlWinModuleExtractCreateWndData  
 Llame a esta función para extraer una estructura `_AtlCreateWndData` existente.  
 
```
ATLINLINE ATLAPI_(void*) AtlWinModuleExtractCreateWndData(_ATL_WIN_MODULE* pWinModule);
```  
  
### <a name="parameters"></a>Parámetros  
 `pWinModule`  
 Puntero a un módulo [_ATL_WIN_MODULE70](../../atl/reference/atl-win-module70-structure.md) estructura.  
  
### <a name="return-value"></a>Valor devuelto  
 Devuelve un puntero a la [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) estructura.  
  
### <a name="remarks"></a>Comentarios  
 Esta función extraerá existente `_AtlCreateWndData` estructura de la lista que hace referencia a un módulo `_ATL_WIN_MODULE70` estructura.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)

