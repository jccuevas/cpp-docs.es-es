---
title: Estructura de _ATL_WIN_MODULE70 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 72f621af04dc420587c2660313aecf70adfaa1ec
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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





