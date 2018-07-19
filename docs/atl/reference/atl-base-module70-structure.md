---
title: Estructura de _ATL_BASE_MODULE70 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 484fc4a68d0421cb12e901b2d56f30e95f6cb79b
ms.sourcegitcommit: 19a108b4b30e93a9ad5394844c798490cb3e2945
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34256423"
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
 [Clases y structs](../../atl/reference/atl-classes.md)





