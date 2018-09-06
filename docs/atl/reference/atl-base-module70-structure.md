---
title: _ATL_BASE_MODULE70 (estructura) | Microsoft Docs
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
ms.openlocfilehash: fb7218d7fc8886cffdcce13f09a682fdc635f84f
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43759933"
---
# <a name="atlbasemodule70-structure"></a>_ATL_BASE_MODULE70 (estructura)

Usado por cualquier proyecto que usa ATL.

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
El tamaño de la estructura que se utiliza para el control de versiones.

`m_hInst`  
El `hInstance` para este módulo (exe o dll).

`m_hInstResource`  
Identificador de recurso de instancia predeterminado.

`m_bNT5orWin98`  
Información de versión del sistema operativo. Lo utiliza internamente ATL.

`dwAtlBuildVer`  
Almacena la versión de ATL. Actualmente 0x0700.

`pguidVer`  
GUID interno de ATL.

`m_csResource`  
Usar para sincronizar el acceso a la `m_rgResourceInstance` matriz. Lo utiliza internamente ATL.

`m_rgResourceInstance`  
Matriz utilizada para buscar recursos en todas las instancias de recursos de los que es compatible con ATL. Lo utiliza internamente ATL.

## <a name="remarks"></a>Comentarios

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) se define como un typedef de _ATL_BASE_MODULE70.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="see-also"></a>Vea también

[Clases y structs](../../atl/reference/atl-classes.md)

