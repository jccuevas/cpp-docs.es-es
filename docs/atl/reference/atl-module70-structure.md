---
title: Estructura de _ATL_MODULE70 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
caps.latest.revision: 16
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
ms.openlocfilehash: ea1d87d3d500fc08f3da16de6820ca003e899419
ms.lasthandoff: 02/24/2017

---
# <a name="atlmodule70-structure"></a>_ATL_MODULE70 (estructura)
Contiene los datos utilizados por cada módulo ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```  
  
## <a name="members"></a>Miembros  
 `cbSize`  
 El tamaño de la estructura, utilizada para el control de versiones.  
  
 `m_nLockCnt`  
 Recuento de referencias para determinar cuánto tiempo permanecerá activo el módulo.  
  
 **m_pTermFuncs**  
 Funciones de pistas que se han registrado para llamar cuando se cierra ATL.  
  
 **m_csStaticDataInitAndTypeInfo**  
 Se usa para coordinar el acceso a datos internos en situaciones de multiproceso.  
  
## <a name="remarks"></a>Comentarios  
 [_ATL_MODULE](atl-typedefs.md#_atl_module) se define como un typedef de `_ATL_MODULE70`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)








