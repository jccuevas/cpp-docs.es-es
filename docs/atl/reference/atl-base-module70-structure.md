---
title: Estructura de _ATL_BASE_MODULE70
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_BASE_MODULE70
- ATL._ATL_BASE_MODULE70
- _ATL_BASE_MODULE70
helpviewer_keywords:
- ATL_BASE_MODULE70 structure
- _ATL_BASE_MODULE70 structure
ms.assetid: 4539282f-15b8-4d7c-aafa-a85dc56f4980
ms.openlocfilehash: 3893e4ce4fcd24f48d9e981ad24505f82dc98833
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168649"
---
# <a name="_atl_base_module70-structure"></a>Estructura de _ATL_BASE_MODULE70

Lo utiliza cualquier proyecto que use ATL.

## <a name="syntax"></a>Sintaxis

```cpp
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

## <a name="members"></a>Members

`cbSize`<br/>
Tamaño de la estructura, que se usa para el control de versiones.

`m_hInst`<br/>
`hInstance` Para este módulo (exe o dll).

`m_hInstResource`<br/>
Identificador de recurso de instancia predeterminado.

`m_bNT5orWin98`<br/>
Información de versión del sistema operativo. Lo utiliza internamente ATL.

`dwAtlBuildVer`<br/>
Almacena la versión de ATL. 0x0700 actualmente.

`pguidVer`<br/>
GUID interno de ATL.

`m_csResource`<br/>
Se utiliza para sincronizar el `m_rgResourceInstance` acceso a la matriz. Lo utiliza internamente ATL.

`m_rgResourceInstance`<br/>
Matriz utilizada para buscar recursos en todas las instancias de recursos de las que ATL es consciente. Lo utiliza internamente ATL.

## <a name="remarks"></a>Observaciones

[_ATL_BASE_MODULE](atl-typedefs.md#_atl_base_module) se define como una definición de tipo de _ATL_BASE_MODULE70.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcore. h

## <a name="see-also"></a>Consulte también

[Clases y estructuras](../../atl/reference/atl-classes.md)
