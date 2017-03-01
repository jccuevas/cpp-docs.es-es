---
title: Estructura de _ATL_WIN_MODULE70 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
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
ms.sourcegitcommit: 4e393abb2a904a0f5e101efe3d78d0645664397b
ms.openlocfilehash: 383384c8f08b98592f92b5d38850137c1c0c6d54
ms.lasthandoff: 02/24/2017

---
# <a name="atlwinmodule70-structure"></a>_ATL_WIN_MODULE70 (estructura)
Use el código de ventanas en ATL.  
  
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
 El tamaño de la estructura, utilizada para el control de versiones.  
  
 `m_csWindowCreate`  
 Se utiliza para serializar el acceso a código de registro de la ventana. Utilizada internamente por ATL.  
  
 **m_pCreateWndList**  
 Se utiliza para enlazar a sus objetos de windows. Utilizada internamente por ATL.  
  
 **m_rgWindowClassAtoms**  
 Se utiliza para realizar un seguimiento de los registros de clase de ventana para que puedan estar registrados correctamente en la finalización. Utilizada internamente por ATL.  
  
## <a name="remarks"></a>Comentarios  
 [_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) se define como un typedef de `_ATL_WIN_MODULE70`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)






