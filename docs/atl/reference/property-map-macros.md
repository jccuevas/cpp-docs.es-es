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
ms.openlocfilehash: 1e2e7235dd924467d9d5e0613a704fedf8340ae4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62197273"
---
# <a name="property-map-macros"></a>Macros de mapa de propiedades

Estas macros definen asignaciones de propiedad y entradas.

|||
|-|-|
|[BEGIN_PROP_MAP](#begin_prop_map)|Marca el principio de la asignación de propiedades ATL.|
|[PROP_DATA_ENTRY](#prop_data_entry)|Indica la extensión o dimensiones de un control ActiveX.|
|[PROP_ENTRY_TYPE](#prop_entry_type)|Escribe una descripción, la propiedad DISPID y la propiedad página de propiedades CLSID en la asignación de propiedad.|
|[PROP_ENTRY_TYPE_EX](#prop_entry_type_ex)|Escribe una descripción de propiedad, propiedad DISPID, CLSID, de página de propiedades y `IDispatch` IID en la asignación de propiedad.|
|[PROP_PAGE](#prop_page)|Escribe una CLSID de la página de propiedades en la asignación de propiedad.|
|[END_PROP_MAP](#end_prop_map)|Marca el final de la asignación de propiedades ATL.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="begin_prop_map"></a>  BEGIN_PROP_MAP

Marca el principio de la asignación de propiedad del objeto.

```
BEGIN_PROP_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
[in] Especifica la clase que contiene la asignación de propiedad.

### <a name="remarks"></a>Comentarios

La asignación de propiedad almacena las descripciones de propiedad, propiedad DISPID, CLSID, de página de propiedades y `IDispatch` IID. Las clases [IPerPropertyBrowsingImpl](../../atl/reference/iperpropertybrowsingimpl-class.md), [IPersistPropertyBagImpl](../../atl/reference/ipersistpropertybagimpl-class.md), [IPersistStreamInitImpl](../../atl/reference/ipersiststreaminitimpl-class.md), y [ISpecifyPropertyPagesImpl](../../atl/reference/ispecifypropertypagesimpl-class.md)usar la asignación de propiedad para recuperar y establecer esta información.

Cuando se crea un objeto con el Asistente para proyectos ATL, el asistente creará un mapa de propiedades vacía especificando BEGIN_PROP_MAP seguido [END_PROP_MAP](#end_prop_map).

No guardar BEGIN_PROP_MAP out de la extensión (es decir, las dimensiones) de un mapa de propiedades, porque un objeto mediante una asignación de propiedad no puede tener una interfaz de usuario, por lo que no tendría ninguna extensión. Si el objeto es un control ActiveX con una interfaz de usuario, tiene una extensión. En este caso, debe especificar [PROP_DATA_ENTRY](#prop_data_entry) en la asignación de propiedad para proporcionar la medida.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#103](../../atl/codesnippet/cpp/property-map-macros_1.h)]

##  <a name="prop_data_entry"></a>  PROP_DATA_ENTRY

Indica la extensión o dimensiones de un control ActiveX.

```
PROP_DATA_ENTRY( szDesc, member, vt)
```

### <a name="parameters"></a>Parámetros

*szDesc*<br/>
[in] Descripción de propiedad.

*member*<br/>
[in] El miembro de datos que contiene la extensión; Por ejemplo, `m_sizeExtent`.

*vt*<br/>
[in] Especifica el tipo de variante de la propiedad.

### <a name="remarks"></a>Comentarios

Esta macro hace que el miembro de datos especificado que se deben conservar.

Cuando se crea un control ActiveX, el asistente inserta esta macro después de la macro de asignación de propiedad [BEGIN_PROP_MAP](#begin_prop_map) y antes de la macro de asignación de propiedad [END_PROP_MAP](#end_prop_map).

### <a name="example"></a>Ejemplo

En el ejemplo siguiente, la extensión del objeto (`m_sizeExtent`) es que se hace persistente.

[!code-cpp[NVC_ATL_Windowing#131](../../atl/codesnippet/cpp/property-map-macros_2.h)]

[!code-cpp[NVC_ATL_Windowing#132](../../atl/codesnippet/cpp/property-map-macros_3.h)]

##  <a name="prop_entry_type"></a>  PROP_ENTRY_TYPE

Use esta macro para escribir una descripción, la propiedad DISPID y la propiedad página de propiedades CLSID en mapa de propiedades del objeto.

```
PROP_ENTRY_TYPE( szDesc, dispid, clsid, vt)
```

### <a name="parameters"></a>Parámetros

*szDesc*<br/>
[in] Descripción de propiedad.

*dispid*<br/>
[in] DISPID de la propiedad.

*clsid*<br/>
[in] El CLSID de la página de propiedades asociado. Utilice el valor especial CLSID_NULL para una propiedad que no tiene una página de propiedades asociado.

*vt*<br/>
[in] El tipo de propiedad.

### <a name="remarks"></a>Comentarios

La macro PROP_ENTRY era inseguro y en desuso. Se ha reemplazado con PROP_ENTRY_TYPE.

El [BEGIN_PROP_MAP](#begin_prop_map) macro marca el principio de la asignación de propiedad; la [END_PROP_MAP](#end_prop_map) macro marca el final.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_PROP_MAP](#begin_prop_map).

##  <a name="prop_entry_type_ex"></a>  PROP_ENTRY_TYPE_EX

Similar a [PROP_ENTRY_TYPE](#prop_entry_type), pero le permite especificar un IID determinado si el objeto es compatible con varias interfaces duales.

```
PROP_ENTRY_TYPE_EX( szDesc, dispid, clsid, iidDispatch, vt)
```

### <a name="parameters"></a>Parámetros

*szDesc*<br/>
[in] Descripción de propiedad.

*dispid*<br/>
[in] DISPID de la propiedad.

*clsid*<br/>
[in] El CLSID de la página de propiedades asociado. Utilice el valor especial CLSID_NULL para una propiedad que no tiene una página de propiedades asociado.

*iidDispatch*<br/>
[in] IID de la definición de la propiedad de interfaz dual.

*vt*<br/>
[in] El tipo de propiedad.

### <a name="remarks"></a>Comentarios

La macro PROP_ENTRY_EX era inseguro y en desuso. Se ha reemplazado con PROP_ENTRY_TYPE_EX.

El [BEGIN_PROP_MAP](#begin_prop_map) macro marca el principio de la asignación de propiedad; la [END_PROP_MAP](#end_prop_map) macro marca el final.

### <a name="example"></a>Ejemplo

En el ejemplo siguiente se agrupan las entradas de `IMyDual1` seguido de una entrada para `IMyDual2`. La agrupación por interfaz dual mejorará el rendimiento.

[!code-cpp[NVC_ATL_Windowing#133](../../atl/codesnippet/cpp/property-map-macros_4.h)]

##  <a name="prop_page"></a>  PROP_PAGE

Use esta macro para formalizar una CLSID de la página de propiedades de asignación de propiedad del objeto.

```
PROP_PAGE(clsid)
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
[in] El CLSID de una página de propiedades.

### <a name="remarks"></a>Comentarios

Es similar a PROP_PAGE [PROP_ENTRY_TYPE](#prop_entry_type), pero no requiere una descripción de la propiedad o el DISPID.

> [!NOTE]
>  Si ya ha introducido un CLSID con PROP_ENTRY_TYPE o [PROP_ENTRY_TYPE_EX](#prop_entry_type_ex), no es necesario realizar una entrada adicional con PROP_PAGE.

El [BEGIN_PROP_MAP](#begin_prop_map) macro marca el principio de la asignación de propiedad; la [END_PROP_MAP](#end_prop_map) macro marca el final.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#134](../../atl/codesnippet/cpp/property-map-macros_5.h)]

##  <a name="end_prop_map"></a>  END_PROP_MAP

Marca el final de la asignación de propiedad del objeto.

```
END_PROP_MAP()
```

### <a name="remarks"></a>Comentarios

Cuando se crea un objeto con el Asistente para proyectos ATL, el asistente creará un mapa de propiedades vacía especificando [BEGIN_PROP_MAP](#begin_prop_map) seguido END_PROP_MAP.

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_PROP_MAP](#begin_prop_map).

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
