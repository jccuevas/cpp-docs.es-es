---
title: Estructura de _ATL_MODULE70
ms.date: 11/04/2016
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
ms.openlocfilehash: 8d39cdd281e09cdfe09546627aa630a11d12464e
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168571"
---
# <a name="_atl_module70-structure"></a>Estructura de _ATL_MODULE70

Contiene los datos utilizados por cada módulo ATL.

## <a name="syntax"></a>Sintaxis

```cpp
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>Members

`cbSize`<br/>
Tamaño de la estructura, que se usa para el control de versiones.

`m_nLockCnt`<br/>
Recuento de referencias para determinar cuánto tiempo debe permanecer activo el módulo.

`m_pTermFuncs`<br/>
Realiza un seguimiento de las funciones que se han registrado para que se llamen cuando ATL se cierra.

`m_csStaticDataInitAndTypeInfo`<br/>
Se usa para coordinar el acceso a los datos internos en situaciones multiproceso.

## <a name="remarks"></a>Observaciones

[_ATL_MODULE](atl-typedefs.md#_atl_module) se define como una definición de `_ATL_MODULE70`tipo de.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="see-also"></a>Consulte también

[Clases y estructuras](../../atl/reference/atl-classes.md)
