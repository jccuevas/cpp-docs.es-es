---
title: Estructura de _ATL_BASE_MODULE70 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
dev_langs: C++
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
caps.latest.revision: "15"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 8a85aa23baf294f5f1f4dc2eb49c6004d7633280
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="atlbasemodule70-structure"></a>Estructura de _ATL_BASE_MODULE70
Usando ningún proyecto que usa ATL.  
  
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
 El tamaño de la estructura que se utiliza para controlar las versiones.  
  
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
 Matriz que se utiliza para buscar recursos en todas las instancias de recursos de los cuales es compatible con ATL. Utilizada internamente por ATL.  
  
## <a name="remarks"></a>Comentarios  
 [_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) se define como una definición de tipo de `_ATL_BASE_MODULE70`.  
  
## <a name="requirements"></a>Requisitos  
 **Encabezado:** atlcore.h  
  
## <a name="see-also"></a>Vea también  
 [Estructuras](../../atl/reference/atl-structures.md)





