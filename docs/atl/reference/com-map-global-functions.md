---
title: Funciones globales del mapa COM
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: c4ce7c7a68c0744ad65ef4914088fa12d3340628
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326690"
---
# <a name="com-map-global-functions"></a>Funciones globales del mapa COM

Estas funciones proporcionan `IUnknown` compatibilidad con las implementaciones de mapa COM.

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Delega `IUnknown` en el de un objeto no agregado.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Genera código eficaz para comparar `IUnknown`interfaces con .|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

## <a name="atlinternalqueryinterface"></a><a name="atlinternalqueryinterface"></a>AtlInternalQueryInterface

Recupera un puntero a la interfaz solicitada.

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*pEsto*<br/>
[en] Puntero al objeto que contiene el mapa COM `QueryInterface`de interfaces expuestas a .

*pEntries*<br/>
[en] Matriz de `_ATL_INTMAP_ENTRY` estructuras que tienen acceso a un mapa de interfaces disponibles.

*Iid*<br/>
[en] GUID de la interfaz que se solicita.

*ppvObject*<br/>
[fuera] Un puntero al puntero de interfaz especificado en *iid*, o NULL si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

`AtlInternalQueryInterface` solo administra interfaces de la tabla de asignación COM. Si el objeto se `AtlInternalQueryInterface` agrega, no delega en el desconocido externo. Puede introducir interfaces en la tabla de mapas COM con la [macro COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) o una de sus variantes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

## <a name="inlineisequaliunknown"></a><a name="inlineisequaliunknown"></a>InlineIsEqualIUnknown

Llame a esta función, para `IUnknown`el caso especial de prueba para .

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parámetros

*rguid1*<br/>
[en] El GUID que `IID_IUnknown`se va a comparar con .

## <a name="see-also"></a>Consulte también

[Functions](../../atl/reference/atl-functions.md)<br/>
[Macros de mapas COM](../../atl/reference/com-map-macros.md)
