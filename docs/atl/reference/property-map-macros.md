---
title: Macros de asignación de propiedades
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
ms.openlocfilehash: 1e2e7235dd924467d9d5e0613a704fedf8340ae4
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/16/2020
ms.locfileid: "79422977"
---
# <a name="property-map-macros"></a>Macros de asignación de propiedades

Estas macros definen asignaciones y entradas de propiedades.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Marca el principio del mapa de propiedades de ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Indica la extensión o dimensiones de un control ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Especifica una descripción de propiedad, un DISPID de propiedad y un CLSID de página de propiedades en el mapa de propiedades.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Escribe una descripción de propiedad, un DISPID de propiedad, una página de propiedades CLSID y `IDispatch` IID en la asignación de propiedad.|
|[PROP_PAGE](#prop_page)|Especifica el CLSID de una página de propiedades en la asignación de propiedades.|
|[END_PROP_MAP](#end_prop_map)|Marca el final de la asignación de propiedades ATL.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="begin_prop_map"></a>BEGIN_PROP_MAP

Marca el principio del mapa de propiedades del objeto.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
de Especifica la clase que contiene la asignación de propiedades.

### <a name="remarks"></a>Observaciones

La asignación de propiedades almacena las descripciones de propiedades, los DISPID de propiedad, los CLSID de las páginas de propiedades y `IDispatch` IID. Las clases [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md)y [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md) usan la asignación de propiedad para recuperar y establecer esta información.

Al crear un objeto con el Asistente para proyectos ATL, el asistente creará una asignación de propiedades vacía especificando BEGIN_PROP_MAP seguido de [END_PROP_MAP](#end_prop_map).

BEGIN_PROP_MAP no guarda la extensión (es decir, las dimensiones) de una asignación de propiedad, porque un objeto que usa una asignación de propiedad no puede tener una interfaz de usuario, por lo que no tendría ninguna extensión. Si el objeto es un control ActiveX con una interfaz de usuario, tiene una extensión. En este caso, debe especificar [PROP_DATA_ENTRY](#prop_data_entry) en el mapa de propiedades para proporcionar la extensión.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>PROP_DATA_ENTRY

Indica la extensión o dimensiones de un control ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parámetros

*szDesc*<br/>
de La descripción de la propiedad.

*member*<br/>
de Miembro de datos que contiene la extensión; por ejemplo, `m_sizeExtent`.

*vt*<br/>
de Especifica el tipo VARIANT de la propiedad.

### <a name="remarks"></a>Observaciones

Esta macro hace que el miembro de datos especificado se conserve.

Cuando se crea un control ActiveX, el asistente inserta esta macro después de la macro de asignación de propiedades [BEGIN_PROP_MAP](#begin_prop_map) y antes de que [END_PROP_MAP](#end_prop_map)la macro de asignación de propiedades.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, se conserva la extensión del objeto (`m_sizeExtent`).

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>PROP_ENTRY_TYPE

Utilice esta macro para escribir una descripción de propiedad, un DISPID de propiedad y un CLSID de página de propiedades en el mapa de propiedades del objeto.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parámetros

*szDesc*<br/>
de La descripción de la propiedad.

*DISPID*<br/>
de El DISPID de la propiedad.

*CLSID*<br/>
de CLSID de la página de propiedades asociada. Use el valor especial CLSID_NULL para una propiedad que no tenga una página de propiedades asociada.

*vt*<br/>
de Tipo de la propiedad.

### <a name="remarks"></a>Observaciones

La macro PROP_ENTRY era insegura y quedó en desuso. Se ha reemplazado por PROP_ENTRY_TYPE.

La macro [BEGIN_PROP_MAP](#begin_prop_map) marca el principio del mapa de propiedades; la macro [END_PROP_MAP](#end_prop_map) marca el final.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_PROP_MAP](#begin_prop_map).

##  <a name="prop_entry_type_ex"></a>PROP_ENTRY_TYPE_EX

Similar a [PROP_ENTRY_TYPE](#prop_entry_type), pero permite especificar un IID determinado si el objeto admite varias interfaces duales.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parámetros

*szDesc*<br/>
de La descripción de la propiedad.

*DISPID*<br/>
de El DISPID de la propiedad.

*CLSID*<br/>
de CLSID de la página de propiedades asociada. Use el valor especial CLSID_NULL para una propiedad que no tenga una página de propiedades asociada.

*iidDispatch*<br/>
de IID de la interfaz dual que define la propiedad.

*vt*<br/>
de Tipo de la propiedad.

### <a name="remarks"></a>Observaciones

La macro PROP_ENTRY_EX era insegura y quedó en desuso. Se ha reemplazado por PROP_ENTRY_TYPE_EX.

La macro [BEGIN_PROP_MAP](#begin_prop_map) marca el principio del mapa de propiedades; la macro [END_PROP_MAP](#end_prop_map) marca el final.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se agrupan entradas para `IMyDual1` seguido de una entrada para `IMyDual2`. La agrupación por interfaz dual mejorará el rendimiento.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>PROP_PAGE

Utilice esta macro para especificar un CLSID de página de propiedades en el mapa de propiedades del objeto.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parámetros

*CLSID*<br/>
de CLSID de una página de propiedades.

### <a name="remarks"></a>Observaciones

PROP_PAGE es similar a [PROP_ENTRY_TYPE](#prop_entry_type), pero no requiere una descripción de propiedad o un DispId.

> [!NOTE]
>  Si ya ha especificado un CLSID con PROP_ENTRY_TYPE o [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), no es necesario que realice una entrada adicional con PROP_PAGE.

La macro [BEGIN_PROP_MAP](#begin_prop_map) marca el principio del mapa de propiedades; la macro [END_PROP_MAP](#end_prop_map) marca el final.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>END_PROP_MAP

Marca el final del mapa de propiedades del objeto.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Observaciones

Al crear un objeto con el Asistente para proyectos ATL, el asistente creará una asignación de propiedades vacía especificando [BEGIN_PROP_MAP](#begin_prop_map) seguido de END_PROP_MAP.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
