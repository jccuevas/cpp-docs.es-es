---
title: Estructura de _ATL_MODULE70 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: f189ef58ab83a6e77852c109e6da3ae86dc5555d
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
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







