---
title: Macros de categoría
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 9c74b1e8e9fc101ed9b3acd842d38dcdb9eb48f3
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818497"
---
# <a name="category-macros"></a>Macros de categoría

Estas macros definen asignaciones de categoría.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Marca el principio de la asignación de categoría.|
|[END_CATEGORY_MAP](#end_category_map)|Marca el final de la asignación de categoría.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Indica las categorías que se implementan mediante el objeto COM.|
|[REQUIRED_CATEGORY](#required_category)|Indica las categorías que son necesarias del contenedor por el objeto COM.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP

Marca el principio de la asignación de categoría.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
[in] El nombre de la clase que contiene la asignación de categoría.

### <a name="remarks"></a>Comentarios

La asignación de categoría se usa para especificar qué categorías de componentes se implementará la clase COM y las categorías que requiere de su contenedor.

Agregar un [IMPLEMENTED_CATEGORY](#implemented_category) entrada a la asignación para cada categoría implementada por la clase COM. Agregar un [REQUIRED_CATEGORY](#required_category) entrada a la asignación para cada categoría de la clase requiere que sus clientes a implementar. Marcar el final de la asignación con el [END_CATEGORY_MAP](#end_category_map) macro.

Las categorías de componentes aparece en el mapa se registrará automáticamente cuando el módulo se registra si la clase tiene asociada una [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) .

> [!NOTE]
>  ATL usa el Administrador de componentes estándar de categorías para registrar las categorías de componentes. Si el administrador no está presente en el sistema cuando se registra el módulo, registro es satisfactorio, pero no se registrarán las categorías del componente para esa clase.

Para obtener más información acerca de las categorías del componente, vea [¿qué categorías de componentes y cómo funcionan](/windows/desktop/com/component-categories-and-how-they-work) en el SDK de Windows.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>  END_CATEGORY_MAP

Marca el final de la asignación de categoría.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_CATEGORY_MAP](#begin_category_map).

##  <a name="implemented_category"></a>  IMPLEMENTED_CATEGORY

Agregar una macro IMPLEMENTED_CATEGORY a su componente [mapa categoría](#begin_category_map) para especificar que debe registrarse como implementación de la categoría identificada por la *catID* parámetro.

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parámetros

*catID*<br/>
[in] CATID constante o variable que contiene el identificador único global (GUID) para la categoría de implementada. La dirección de *catID* serán tomadas y se agregarán al mapa. Consulte la tabla siguiente para una selección de categorías de cotizaciones.

### <a name="remarks"></a>Comentarios

Las categorías de componentes aparece en el mapa se registrará automáticamente cuando el módulo se registra si la clase tiene asociada una [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.

Los clientes pueden usar la información de categoría registrada para la clase para determinar sus capacidades y requisitos sin tener que crear una instancia de ella.

Para obtener más información acerca de las categorías del componente, vea [¿qué categorías de componentes y cómo funcionan](/windows/desktop/com/component-categories-and-how-they-work) en el SDK de Windows.

### <a name="a-selection-of-stock-categories"></a>Una selección de categorías de cotizaciones

|Descripción|Símbolo|GUID del registro|
|-----------------|------------|-------------------|
|Seguros para Scripting|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Seguro para inicialización|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Contención de sitio de marco simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|enlace de datos simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Enlace de datos avanzado|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Controles sin ventana|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objetos orientados a Internet|Consulte [objetos compatibles con Internet](/windows/desktop/com/internet-aware-objects) en el SDK de Windows para obtener una lista de ejemplo.||

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>  REQUIRED_CATEGORY

Agregar una macro REQUIRED_CATEGORY a su componente [mapa categoría](#begin_category_map) para especificar que debe registrarse como que requiere la categoría identificada por la *catID* parámetro.

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parámetros

*catID*<br/>
[in] CATID constante o variable que contiene el identificador único global (GUID) para la categoría necesaria. La dirección de *catID* serán tomadas y se agregarán al mapa. Consulte la tabla siguiente para una selección de categorías de cotizaciones.

### <a name="remarks"></a>Comentarios

Las categorías de componentes aparece en el mapa se registrará automáticamente cuando el módulo se registra si la clase tiene asociada una [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) macro.

Los clientes pueden usar la información de categoría registrada para la clase para determinar sus capacidades y requisitos sin tener que crear una instancia de ella. Por ejemplo, un control puede requerir que un contenedor admiten el enlace de datos. El contenedor puede averiguar si tiene las capacidades necesarias para hospedar el control al consultar el Administrador de categoría para las categorías requeridas por dicho control. Si el contenedor no admite una característica necesaria, puede rechazar alojar el objeto COM.

Para obtener más información acerca de las categorías de componentes, incluida una lista de ejemplo, vea [¿qué categorías de componentes y cómo funcionan](/windows/desktop/com/component-categories-and-how-they-work) en el SDK de Windows.

### <a name="a-selection-of-stock-categories"></a>Una selección de categorías de cotizaciones

|Descripción|Símbolo|GUID del registro|
|-----------------|------------|-------------------|
|Seguros para Scripting|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Seguro para inicialización|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Contención de sitio de marco simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|enlace de datos simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Enlace de datos avanzado|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Controles sin ventana|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objetos orientados a Internet|Consulte [objetos compatibles con Internet](/windows/desktop/com/internet-aware-objects) en el SDK de Windows para obtener una lista de ejemplo.||

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
