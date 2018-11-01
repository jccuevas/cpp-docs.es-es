---
title: _ATL_BASE_MODULE70 (estructura)
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 806ed86076d8b27662bcd9a328d43cabf5df5c86
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50667550"
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

`cbSize`<br/>
El tamaño de la estructura que se utiliza para el control de versiones.

`m_hInst`<br/>
El `hInstance` para este módulo (exe o dll).

`m_hInstResource`<br/>
Identificador de recurso de instancia predeterminado.

`m_bNT5orWin98`<br/>
Información de versión del sistema operativo. Lo utiliza internamente ATL.

`dwAtlBuildVer`<br/>
Almacena la versión de ATL. Actualmente 0x0700.

`pguidVer`<br/>
GUID interno de ATL.

`m_csResource`<br/>
Usar para sincronizar el acceso a la `m_rgResourceInstance` matriz. Lo utiliza internamente ATL.

`m_rgResourceInstance`<br/>
Matriz utilizada para buscar recursos en todas las instancias de recursos de los que es compatible con ATL. Lo utiliza internamente ATL.

## <a name="remarks"></a>Comentarios

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) se define como un typedef de _ATL_BASE_MODULE70.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore.h

## <a name="see-also"></a>Vea también

[Clases y structs](../../atl/reference/atl-classes.md)

