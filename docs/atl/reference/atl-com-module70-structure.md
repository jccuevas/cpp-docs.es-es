---
title: _ATL_COM_MODULE70 (estructura)
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c6361fc5374ed732cd9ccbfbbd1d3d1c2fc8f1f0
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57261289"
---
# <a name="atlcommodule70-structure"></a>_ATL_COM_MODULE70 (estructura)

Utilizado por el código relacionado con COM de ATL.

## <a name="syntax"></a>Sintaxis

```
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>Miembros

`cbSize`<br/>
El tamaño de la estructura que se utiliza para el control de versiones.

`m_hInstTypeLib`<br/>
La instancia de identificador a la biblioteca de tipos para este módulo.

`m_ppAutoObjMapFirst`<br/>
Dirección del elemento de matriz que indica el principio de las entradas de asignación de objeto para este módulo.

`m_ppAutoObjMapLast`<br/>
Dirección del elemento de matriz que indica el final de las entradas de asignación de objeto para este módulo.

`m_csObjMap`<br/>
Sección crítica para serializar el acceso a las entradas de asignación de objeto. Lo utiliza internamente ATL.

## <a name="remarks"></a>Comentarios

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) se define como un typedef de _ATL_COM_MODULE70.

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="see-also"></a>Vea también

[Clases y structs](../../atl/reference/atl-classes.md)
