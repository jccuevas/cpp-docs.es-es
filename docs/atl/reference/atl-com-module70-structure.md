---
title: _ATL_COM_MODULE70 Structure | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: reference
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 573bf43c783a1fb5dbd0eca364fedddb9bafbac7
ms.sourcegitcommit: 6002df0ac79bde5d5cab7bbeb9d8e0ef9920da4a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/14/2018
---
# <a name="atlcommodule70-structure"></a>_ATL_COM_MODULE70 Structure
Utilizado por el código relacionado con COM de ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```  
  
## <a name="members"></a>Miembros  
 `cbSize`  
 El tamaño de la estructura que se utiliza para controlar las versiones.  
  
 `m_hInstTypeLib`  
 La instancia de identificador a la biblioteca de tipos para este módulo.  
  
 **m_ppAutoObjMapFirst**  
 Dirección del elemento de matriz que indica el principio de las entradas de asignación de objeto para este módulo.  
  
 **m_ppAutoObjMapLast**  
 Dirección del elemento de matriz que indica el final de las entradas de asignación de objeto para este módulo.  
  
 `m_csObjMap`  
 Sección crítica para serializar el acceso a las entradas de asignación de objeto. Utilizada internamente por ATL.  
  
## <a name="remarks"></a>Comentarios  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) se define como una definición de tipo de `_ATL_COM_MODULE70`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)





