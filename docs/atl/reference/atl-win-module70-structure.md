---
title: Estructura de _ATL_WIN_MODULE70
ms.date: 11/04/2016
f1_keywords:
- _ATL_WIN_MODULE70
- ATL::_ATL_WIN_MODULE70
- ATL._ATL_WIN_MODULE70
helpviewer_keywords:
- _ATL_WIN_MODULE70 structure
- ATL_WIN_MODULE70 structure
ms.assetid: a0aaf3ea-ca77-46ec-bd53-4dfb61dffbea
ms.openlocfilehash: 770e78e4ad87338528aa654f5ecaa08b45315846
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168558"
---
# <a name="_atl_win_module70-structure"></a>Estructura de _ATL_WIN_MODULE70

Lo utiliza el código de ventana en ATL.

## <a name="syntax"></a>Sintaxis

```cpp
struct _ATL_WIN_MODULE70 {
    UNIT cbSize;
    CRITICAL_SECTION m_csWindowCreate;
    _AtlCreateWndData* m_pCreateWndList;
    CSimpleArray<ATOM> m_rgWindowClassAtoms;
};
```

## <a name="members"></a>Members

`cbSize`<br/>
Tamaño de la estructura, que se usa para el control de versiones.

`m_csWindowCreate`<br/>
Se usa para serializar el acceso al código de registro de la ventana. Lo utiliza internamente ATL.

`m_pCreateWndList`<br/>
Se utiliza para enlazar Windows a sus objetos. Lo utiliza internamente ATL.

`m_rgWindowClassAtoms`<br/>
Se utiliza para realizar el seguimiento de los registros de clase de ventana para que se pueda anular correctamente el registro en la terminación. Lo utiliza internamente ATL.

## <a name="remarks"></a>Observaciones

[_ATL_WIN_MODULE](atl-typedefs.md#_atl_win_module) se define como una definición de `_ATL_WIN_MODULE70`tipo de.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="see-also"></a>Consulte también

[Clases y estructuras](../../atl/reference/atl-classes.md)
