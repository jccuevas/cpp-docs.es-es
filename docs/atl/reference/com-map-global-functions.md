---
title: Funciones globales de mapa COM
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlInternalQueryInterface
- atlbase/ATL::InlineIsEqualIUnknown
helpviewer_keywords:
- COM interfaces, COM map global functions
ms.assetid: b9612d30-eb23-46ef-8093-d56f237d3cf1
ms.openlocfilehash: 75d081674fa4b63e66f1296834d3de305665ab9a
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57271624"
---
# <a name="com-map-global-functions"></a>Funciones globales de mapa COM

Estas funciones proporcionan compatibilidad para mapa COM `IUnknown` implementaciones.

|||
|-|-|
|[AtlInternalQueryInterface](#atlinternalqueryinterface)|Delega en el `IUnknown` de un objeto no agregado.|
|[InlineIsEqualIUnknown](#inlineisequaliunknown)|Genera un código eficaz para comparar las interfaces con `IUnknown`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlbase.h

##  <a name="atlinternalqueryinterface"></a>  AtlInternalQueryInterface

Recupera un puntero a la interfaz solicitada.

```
HRESULT AtlInternalQueryInterface(
    void* pThis,
    const _ATL_INTMAP_ENTRY* pEntries,
    REFIID iid,
    void** ppvObject);
```

### <a name="parameters"></a>Parámetros

*pThis*<br/>
[in] Un puntero al objeto que contiene el mapa COM de las interfaces expuestas a `QueryInterface`.

*pEntries*<br/>
[in] Una matriz de `_ATL_INTMAP_ENTRY` estructuras que tienen acceso a un mapa de las interfaces disponibles.

*iid*<br/>
[in] El GUID de la interfaz que se solicita.

*ppvObject*<br/>
[out] Un puntero al puntero de interfaz especificado en *iid*, o NULL si no se encuentra la interfaz.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

`AtlInternalQueryInterface` solo administra interfaces de la tabla de asignación COM. Si el objeto es agregado, `AtlInternalQueryInterface` no delegar en el desconocido externo. Puede especificar interfaces en el mapa COM con la macro [COM_INTERFACE_ENTRY](com-interface-entry-macros.md#com_interface_entry) o uno de sus variantes.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#94](../../atl/codesnippet/cpp/com-map-global-functions_1.cpp)]

##  <a name="inlineisequaliunknown"></a>  InlineIsEqualIUnknown

Llame a esta función, en el caso especial de prueba para `IUnknown`.

```
BOOL InlineIsEqualUnknown(REFGUID rguid1);
```

### <a name="parameters"></a>Parámetros

*rguid1*<br/>
[in] El GUID que se compara con `IID_IUnknown`.

## <a name="see-also"></a>Vea también

[Funciones](../../atl/reference/atl-functions.md)<br/>
[Macros de mapa COM](../../atl/reference/com-map-macros.md)
