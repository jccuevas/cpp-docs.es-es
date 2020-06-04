---
title: Estructura de _ATL_COM_MODULE70
ms.date: 11/04/2016
f1_keywords:
- ATL::_ATL_COM_MODULE70
- ATL._ATL_COM_MODULE70
- _ATL_COM_MODULE70
helpviewer_keywords:
- _ATL_COM_MODULE70 structure
- ATL_COM_MODULE70 structure
ms.assetid: 5b0b2fd0-bdeb-4c7e-8870-78fa69ace6e6
ms.openlocfilehash: c2e9e3d6695a7fbbcc87c489edf2e96fcdffb835
ms.sourcegitcommit: 2bc15c5b36372ab01fa21e9bcf718fa22705814f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/27/2020
ms.locfileid: "82168636"
---
# <a name="_atl_com_module70-structure"></a>Estructura de _ATL_COM_MODULE70

Lo usa el código relacionado con COM en ATL.

## <a name="syntax"></a>Sintaxis

```cpp
struct _ATL_COM_MODULE70 {
    UINT cbSize;
    HINSTANCE m_hInstTypeLib;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapFirst;
    _ATL_OBJMAP_ENTRY** m_ppAutoObjMapLast;
    CRITICAL_SECTION m_csObjMap;
};
```

## <a name="members"></a>Members

`cbSize`<br/>
Tamaño de la estructura, que se usa para el control de versiones.

`m_hInstTypeLib`<br/>
La instancia del identificador a la biblioteca de tipos para este módulo.

`m_ppAutoObjMapFirst`<br/>
Dirección del elemento de la matriz que indica el principio de las entradas del mapa de objetos para este módulo.

`m_ppAutoObjMapLast`<br/>
Dirección del elemento de la matriz que indica el final de las entradas del mapa de objetos para este módulo.

`m_csObjMap`<br/>
Sección crítica para serializar el acceso a las entradas de asignación de objetos. Lo utiliza internamente ATL.

## <a name="remarks"></a>Observaciones

[_ATL_COM_MODULE](atl-typedefs.md#_atl_com_module) se define como una definición de tipo de _ATL_COM_MODULE70.

## <a name="requirements"></a>Requisitos

**Encabezado:** ATLBase. h

## <a name="see-also"></a>Consulte también

[Clases y estructuras](../../atl/reference/atl-classes.md)
