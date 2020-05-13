---
title: Macros de mapa de propiedades
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_PROP_MAP
- atlcom/ATL::PROP_DATA_ENTRY
- atlcom/ATL::PROP_ENTRY_TYPE
- atlcom/ATL::PROP_ENTRY_TYPE_EX
- atlcom/ATL::PROP_PAGE
- atlcom/ATL::END_PROP_MAP
helpviewer_keywords:
- property maps
ms.assetid: 128bc742-2b98-4b97-a243-684dbb83db77
ms.openlocfilehash: 56fdb02939a99e396b9000705753e2475b80f6dc
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326094"
---
# <a name="property-map-macros"></a>Macros de mapa de propiedades

Estas macros definen asignaciones de propiedades y entradas.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Marca el principio del mapa de propiedades ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Indica la extensión o las dimensiones de un control ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Escribe una descripción de propiedad, una propiedad DISPID y una página de propiedades CLSID en el mapa de propiedades.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Escribe una descripción de propiedad, la propiedad DISPID, la página de propiedades CLSID e `IDispatch` IID en el mapa de propiedades.|
|[PROP_PAGE](#prop_page)|Escribe un CLSID de página de propiedades en el mapa de propiedades.|
|[END_PROP_MAP](#end_prop_map)|Marca el final del mapa de propiedades ATL.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="begin_prop_map"></a><a name="begin_prop_map"></a>BEGIN_PROP_MAP

Marca el principio del mapa de propiedades del objeto.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
[en] Especifica la clase que contiene el mapa de propiedades.

### <a name="remarks"></a>Observaciones

El mapa de propiedades almacena descripciones de propiedades, DISPID de `IDispatch` propiedades, CLSID de página de propiedades y IID. Las clases [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)y [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) usan el mapa de propiedades para recuperar y establecer esta información.

Al crear un objeto con el Asistente para proyectos ATL, el asistente creará un mapa de propiedades vacío especificando BEGIN_PROP_MAP seguido de [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP no guarda la extensión (es decir, las dimensiones) de un mapa de propiedades, porque un objeto que usa un mapa de propiedades puede no tener una interfaz de usuario, por lo que no tendría ninguna extensión. Si el objeto es un control ActiveX con una interfaz de usuario, tiene una extensión. En este caso, debe especificar [PROP_DATA_ENTRY](#prop_data_entry) en el mapa de propiedades para proporcionar la extensión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

## <a name="prop_data_entry"></a><a name="prop_data_entry"></a>PROP_DATA_ENTRY

Indica la extensión o las dimensiones de un control ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parámetros

*szDesc*<br/>
[en] La descripción de la propiedad.

*Miembro*<br/>
[en] El miembro de datos que contiene la extensión; por ejemplo, `m_sizeExtent`.

*vt*<br/>
[en] Especifica el tipo VARIANT de la propiedad.

### <a name="remarks"></a>Observaciones

Esta macro hace que se conserve el miembro de datos especificado.

Al crear un control ActiveX, el asistente inserta esta macro después de la macro de asignación de [propiedades BEGIN_PROP_MAP](#begin_prop_map) y antes de que la macro de asignación de propiedades [END_PROP_MAP](#end_prop_map).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, se`m_sizeExtent`conserva la extensión del objeto ( ).

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

## <a name="prop_entry_type"></a><a name="prop_entry_type"></a>PROP_ENTRY_TYPE

Utilice esta macro para escribir una descripción de propiedad, una propiedad DISPID y una página de propiedades CLSID en el mapa de propiedades del objeto.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parámetros

*szDesc*<br/>
[en] La descripción de la propiedad.

*dispid*<br/>
[en] DISPID de la propiedad.

*clsid*<br/>
[en] El CLSID de la página de propiedades asociada. Utilice el valor especial CLSID_NULL para una propiedad que no tiene una página de propiedades asociada.

*vt*<br/>
[en] El tipo de la propiedad.

### <a name="remarks"></a>Observaciones

La macro PROP_ENTRY no estaba segura y estaba en desuso. Ha sido reemplazado por PROP_ENTRY_TYPE.

La macro [BEGIN_PROP_MAP](#begin_prop_map) marca el principio del mapa de propiedades; la macro [END_PROP_MAP](#end_prop_map) marca el final.

### <a name="example"></a>Ejemplo

Consulte el ejemplo [de BEGIN_PROP_MAP](#begin_prop_map).

## <a name="prop_entry_type_ex"></a><a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Similar a [PROP_ENTRY_TYPE](#prop_entry_type), pero permite especificar un IID determinado si el objeto admite varias interfaces duales.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parámetros

*szDesc*<br/>
[en] La descripción de la propiedad.

*dispid*<br/>
[en] DISPID de la propiedad.

*clsid*<br/>
[en] El CLSID de la página de propiedades asociada. Utilice el valor especial CLSID_NULL para una propiedad que no tiene una página de propiedades asociada.

*iidDispatch*<br/>
[en] El IID de la interfaz dual que define la propiedad.

*vt*<br/>
[en] El tipo de la propiedad.

### <a name="remarks"></a>Observaciones

La macro PROP_ENTRY_EX no estaba segura y estaba en desuso. Ha sido reemplazado por PROP_ENTRY_TYPE_EX.

La macro [BEGIN_PROP_MAP](#begin_prop_map) marca el principio del mapa de propiedades; la macro [END_PROP_MAP](#end_prop_map) marca el final.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente `IMyDual1` se muestran `IMyDual2`las entradas para seguidas de una entrada para . La agrupación por interfaz dual mejorará el rendimiento.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

## <a name="prop_page"></a><a name="prop_page"></a>PROP_PAGE

Utilice esta macro para escribir una página de propiedades CLSID en el mapa de propiedades del objeto.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
[en] El CLSID de una página de propiedades.

### <a name="remarks"></a>Observaciones

PROP_PAGE es similar a [PROP_ENTRY_TYPE](#prop_entry_type), pero no requiere una descripción de propiedad o DISPID.

> [!NOTE]
> Si ya ha introducido un CLSID con PROP_ENTRY_TYPE o [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), no es necesario realizar una entrada adicional con PROP_PAGE.

La macro [BEGIN_PROP_MAP](#begin_prop_map) marca el principio del mapa de propiedades; la macro [END_PROP_MAP](#end_prop_map) marca el final.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

## <a name="end_prop_map"></a><a name="end_prop_map"></a>END_PROP_MAP

Marca el final del mapa de propiedades del objeto.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Observaciones

Al crear un objeto con el Asistente para proyectos ATL, el asistente creará un mapa de propiedades vacío especificando [BEGIN_PROP_MAP](#begin_prop_map) seguido de END_PROP_MAP.

### <a name="example"></a>Ejemplo

Consulte el ejemplo [de BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
