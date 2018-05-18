---
title: Estructura de _AtlCreateWndData | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- ATL::_AtlCreateWndData
- ATL._AtlCreateWndData
- _AtlCreateWndData
dev_langs:
- C++
helpviewer_keywords:
- _AtlCreateWndData structure
- AtlCreateWndData structure
ms.assetid: 76ed5382-bfbf-4b8b-8a29-912688dfd2ae
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 66388c12def72a9da5b5aeb7e4713ca61c23a6e0
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
---
# <a name="atlcreatewnddata-structure"></a>Estructura de _AtlCreateWndData
Esta estructura contiene datos de la instancia de clase en código basado en ventanas en ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
    struct _AtlCreateWndData{
    void* m_pThis;
    DWORD m_dwThreadID;
    _AtlCreateWndData* m_pNext;
};
```  
  
## <a name="members"></a>Miembros  
 **m_pThis**  
 El **esto** puntero usado para obtener acceso a la instancia de clase en los procedimientos de ventana.  
  
 `m_dwThreadID`  
 El identificador del subproceso de la instancia de clase actual.  
  
 **m_pNext**  
 Puntero a la siguiente `_AtlCreateWndData` objeto.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="see-also"></a>Vea también  
 [Clases y structs](../../atl/reference/atl-classes.md)





