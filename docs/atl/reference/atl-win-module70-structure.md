---
title: _ATL_WIN_MODULE70 (estructura)
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 4f1718c76d21f2e13b36c29db785fe989ff6108e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50482528"
---
# <a name="atlwinmodule70-structure"></a>_ATL_WIN_MODULE70 (estructura)

Utilizado por el código basado en ventanas en ATL.

## <a name="syntax"></a>Sintaxis

```
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>Miembros

`cbSize`<br/>
El tamaño de la estructura que se utiliza para el control de versiones.

`m_csWindowCreate`<br/>
Se usa para serializar el acceso a código de registro de la ventana. Lo utiliza internamente ATL.

`m_pCreateWndList`<br/>
Se usa para enlazar a sus objetos de windows. Lo utiliza internamente ATL.

`m_rgWindowClassAtoms`<br/>
Se usa para realizar un seguimiento de los registros de clase de ventana para que se pueden anular el registro correctamente en la finalización. Lo utiliza internamente ATL.

## <a name="remarks"></a>Comentarios

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) se define como un typedef de `_ATL_WIN_MODULE70`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="see-also"></a>Vea también

[Clases y structs](../../atl/reference/atl-classes.md)

