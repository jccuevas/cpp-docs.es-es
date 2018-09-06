---
title: _ATL_MODULE70 (estructura) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- _ATL_MODULE70
- ATL::_ATL_MODULE70
- ATL._ATL_MODULE70
dev_langs:
- C++
helpviewer_keywords:
- ATL_MODULE70 structure
- _ATL_MODULE70 structure
ms.assetid: b059b2c8-dfd1-4ac9-b07d-39df638cc7b3
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e7afe6867f359b334654f58aad39ad7f143dd428
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43764896"
---
# <a name="atlmodule70-structure"></a>_ATL_MODULE70 (estructura)

Contiene los datos utilizados por cada módulo ATL.

## <a name="syntax"></a>Sintaxis

```
struct _ATL_MODULE70 {
    UINT cbSize;
    LONG m_nLockCnt;
    _ATL_TERMFUNC_ELEM* m_pTermFuncs;
    CComCriticalSection m_csStaticDataInitAndTypeInfo;
};
```

## <a name="members"></a>Miembros

`cbSize`  
El tamaño de la estructura que se utiliza para el control de versiones.

`m_nLockCnt`  
Recuento de referencias para determinar cuánto tiempo el módulo debe permanecer activo.

`m_pTermFuncs`  
Funciones de pistas que se han registrado se debe llamar cuando se cierra ATL.

`m_csStaticDataInitAndTypeInfo`  
Se usa para coordinar el acceso a datos internos en situaciones de multiproceso.

## <a name="remarks"></a>Comentarios

[_ATL_MODULE](atl-typedefs.md#_atl_module) se define como un typedef de `_ATL_MODULE70`.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="see-also"></a>Vea también

[Clases y structs](../../atl/reference/atl-classes.md)

