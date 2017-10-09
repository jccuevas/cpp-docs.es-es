---
title: Estructura de _ATL_WIN_MODULE70 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
caps.latest.revision: 15
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: c55726a1728185f699afbac4ba68a6dc0f70c2bf
ms.openlocfilehash: 7f521b418b7d179eb506a5e9df2887addec059ef
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="atlwinmodule70-structure"></a>Estructura de _ATL_WIN_MODULE70
Uso en código basado en ventanas en ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct _ATL_WIN_MODULE70 {
    UNIT cbSize; 
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```  
  
## <a name="members"></a>Miembros  
 `cbSize`  
 El tamaño de la estructura que se utiliza para controlar las versiones.  
  
 `m_csWindowCreate`  
 Se usa para serializar el acceso a código de registro de la ventana. Utilizada internamente por ATL.  
  
 **m_pCreateWndList**  
 Se usa para enlazar windows a sus objetos. Utilizada internamente por ATL.  
  
 **m_rgWindowClassAtoms**  
 Se utiliza para realizar un seguimiento de los registros de clase de ventana para que se pueden eliminar del registro correctamente en la finalización. Utilizada internamente por ATL.  
  
## <a name="remarks"></a>Comentarios  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) se define como una definición de tipo de `_ATL_WIN_MODULE70`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)






