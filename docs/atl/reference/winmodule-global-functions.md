---
title: Funciones globales WinModule | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- atlbase/ATL::AtlWinModuleAddCreateWndData
- atlbase/ATL::AtlWinModuleExtractCreateWndData
dev_langs: C++
ms.assetid: 8ce45a5b-26a7-491f-9096-c09ceca5f2c2
caps.latest.revision: "19"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 5435b9870a396f24cb2aca5889c9fcfbc90d879a
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="winmodule-global-functions"></a>Funciones globales WinModule
Estas funciones proporcionan compatibilidad para `_AtlCreateWndData` las operaciones de la estructura.  
  
> [!IMPORTANT]
>  Las funciones se enumeran en la tabla siguiente no se puede usar en aplicaciones que se ejecutan en el tiempo de ejecución de Windows.  
  
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
 Puntero a la [_AtlCreateWndData](../../atl/reference/atlcreatewnddata-structure.md) estructura que se inicializará y agregará al módulo actual.  
  
 `pObject`  
 Puntero a un objeto **esto** puntero.  
  
### <a name="remarks"></a>Comentarios  
 Inicializa un `_AtlCreateWndData` estructura, que se utiliza para almacenar el **esto** puntero utilizado para hacer referencia a instancias de clase y lo agrega a la lista de un módulo hace referencia `_ATL_WIN_MODULE70` estructura. Llamado por el método [CAtlWinModule::AddCreateWndData](catlwinmodule-class.md#addcreatewnddata).  
  
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
 Esta función extraerá existente `_AtlCreateWndData` estructura de la lista que se hace referencia a un módulo `_ATL_WIN_MODULE70` estructura.  
  
## <a name="see-also"></a>Vea también  
 [Funciones](../../atl/reference/atl-functions.md)
