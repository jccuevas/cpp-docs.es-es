---
title: Estructura de _AtlCreateWndData | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: a5b0811e88188bb29ef3153f739804cbdac66083
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

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
 [Estructuras](../../atl/reference/atl-structures.md)






