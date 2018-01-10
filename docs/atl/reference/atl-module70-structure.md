---
title: Estructura de _ATL_MODULE70 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs: C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
caps.latest.revision: "16"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: c8122f733282fa819c3d789a90e60171ee006e27
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atlmodule70-structure"></a>Estructura de _ATL_MODULE70
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
 El tamaño de la estructura que se utiliza para controlar las versiones.  
  
 `m_nLockCnt`  
 Recuento de referencias para determinar cuánto tiempo permanecerá activo el módulo.  
  
 **m_pTermFuncs**  
 Funciones de las pistas que se han registrado para llamar cuando se cierra ATL.  
  
 **m_csStaticDataInitAndTypeInfo**  
 Se usa para coordinar el acceso a datos internos en situaciones de multiproceso.  
  
## <a name="remarks"></a>Comentarios  
 [_ATL_MODULE](atl-typedefs.md#_atl_module) se define como una definición de tipo de `_ATL_MODULE70`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)







