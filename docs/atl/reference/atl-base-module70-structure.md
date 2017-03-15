---
title: Estructura de _ATL_BASE_MODULE70 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
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
ms.sourcegitcommit: 347e7bf7cd9173fb2815f44fc052ec23ab4055a6
ms.openlocfilehash: 7456d441d7b3fb74f404f29c893c492feab10ed9
ms.lasthandoff: 02/24/2017

---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 (estructura)
Utilizado por cualquier proyecto que utilice ATL.  
  
## <a name="syntax"></a>Sintaxis  
  
```
struct _ATL_BASE_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInst;
    HINSTANCE m_hInstResource;
    bool m_bNT5orWin98;
    DWORD dwAtlBuildVer;
    GUID* pguidVer;
    CRITICAL_SECTION m_csResource;
    CSimpleArray<HINSTANCE> m_rgResourceInstance;
};
```  
  
## <a name="members"></a>Miembros  
 `cbSize`  
 El tamaño de la estructura, utilizada para el control de versiones.  
  
 `m_hInst`  
 El **hInstance** para este módulo (exe o dll).  
  
 `m_hInstResource`  
 Identificador de recurso de instancia predeterminado.  
  
 **m_bNT5orWin98**  
 Información de versión del sistema operativo. Utilizada internamente por ATL.  
  
 **dwAtlBuildVer**  
 Almacena la versión de ATL. Actualmente 0x0700.  
  
 **pguidVer**  
 GUID interno de ATL.  
  
 **m_csResource**  
 Usar para sincronizar el acceso a la **m_rgResourceInstance** matriz. Utilizada internamente por ATL.  
  
 **m_rgResourceInstance**  
 Matriz que se utiliza para buscar recursos en todas las instancias de recursos de los que es compatible con ATL. Utilizada internamente por ATL.  
  
## <a name="remarks"></a>Comentarios  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) se define como un typedef de `_ATL_BASE_MODULE70`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)






