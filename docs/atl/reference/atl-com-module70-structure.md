---
title: Estructura de _ATL_COM_MODULE70 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
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
ms.translationtype: Machine Translation
ms.sourcegitcommit: 4e393abb2a904a0f5e101efe3d78d0645664397b
ms.openlocfilehash: 503c2a29cf0e70020b012911c51b056f00562374
ms.contentlocale: es-es
ms.lasthandoff: 02/24/2017

---
# <a name="atlcommodule70-structure"></a>_ATL_COM_MODULE70 (estructura)
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
 El tamaño de la estructura, utilizada para el control de versiones.  
  
 `m_hInstTypeLib`  
 La instancia de controlador a la biblioteca de tipos para este módulo.  
  
 **m_ppAutoObjMapFirst**  
 Dirección del elemento de matriz que indica el principio de las entradas de mapa de objeto para este módulo.  
  
 **m_ppAutoObjMapLast**  
 Dirección del elemento de matriz que indica el final de las entradas de mapa de objeto para este módulo.  
  
 `m_csObjMap`  
 Sección crítica para serializar el acceso a las entradas de mapa de objeto. Utilizada internamente por ATL.  
  
## <a name="remarks"></a>Comentarios  
 [_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) se define como un typedef de `_ATL_COM_MODULE70`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlbase.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)






