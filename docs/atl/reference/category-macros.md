---
title: Macros de categoría
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 411e06cc795827eef356018ba427510fd9eb7c06
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69497853"
---
# <a name="category-macros"></a>Macros de categoría

Estas macros definen las asignaciones de categorías.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Marca el principio del mapa de categorías.|
|[END_CATEGORY_MAP](#end_category_map)|Marca el final del mapa de categorías.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Indica las categorías implementadas por el objeto COM.|
|[REQUIRED_CATEGORY](#required_category)|Indica las categorías que el objeto COM necesita del contenedor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="begin_category_map"></a>  BEGIN_CATEGORY_MAP

Marca el principio del mapa de categorías.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*Clase*<br/>
de Nombre de la clase que contiene la asignación de categorías.

### <a name="remarks"></a>Comentarios

El mapa de categorías se usa para especificar qué categorías de componentes implementará la clase COM y qué categorías requiere de su contenedor.

Agregue una entrada [IMPLEMENTED_CATEGORY](#implemented_category) a la asignación para cada categoría implementada por la clase com. Agregue una entrada [REQUIRED_CATEGORY](#required_category) a la asignación para cada categoría que la clase requiera que implementen sus clientes. Marque el final del mapa con la macro [END_CATEGORY_MAP](#end_category_map) .

Las categorías de componentes enumeradas en el mapa se registrarán automáticamente cuando el módulo se registre si la clase tiene un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)asociado.

> [!NOTE]
>  ATL utiliza el administrador de categorías de componentes estándar para registrar categorías de componentes. Si el administrador no está presente en el sistema cuando se registra el módulo, el registro se realiza correctamente, pero las categorías de componentes no se registrarán para esa clase.

Para obtener más información sobre las categorías de componentes, vea [¿Qué son las categorías de componentes y cómo funcionan](/windows/win32/com/component-categories-and-how-they-work) en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="end_category_map"></a>  END_CATEGORY_MAP

Marca el final del mapa de categorías.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Ejemplo

Vea el ejemplo de [BEGIN_CATEGORY_MAP](#begin_category_map).

##  <a name="implemented_category"></a>IMPLEMENTED_CATEGORY

Agregue una macro IMPLEMENTED_CATEGORY al [mapa de categorías](#begin_category_map) del componente para especificar que se debe registrar como la implementación de la categoría identificada por el parámetro *CATID* .

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parámetros

*catID*<br/>
de Una constante CATId o variable que contiene el identificador único global (GUID) para la categoría implementada. Se tomará la dirección de CATID y se agregará a la asignación. Vea la tabla siguiente para obtener una selección de categorías de acciones.

### <a name="remarks"></a>Comentarios

Las categorías de componentes enumeradas en el mapa se registrarán automáticamente cuando el módulo se registre si la clase tiene una macro [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) asociada.

Los clientes pueden usar la información de categoría registrada para la clase con el fin de determinar sus capacidades y requisitos sin tener que crear una instancia del mismo.

Para obtener más información sobre las categorías de componentes, vea [¿Qué son las categorías de componentes y cómo funcionan](/windows/win32/com/component-categories-and-how-they-work) en el Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Selección de categorías de acciones

|DESCRIPCIÓN|Símbolo|GUID del registro|
|-----------------|------------|-------------------|
|Safe para scripting|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Safe para la inicialización|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Contención de sitio de marco simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|enlace de datos simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Enlace de datos avanzado|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Controles sin ventana|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objetos que reconocen Internet|Consulte [objetos con reconocimiento de Internet](/windows/win32/com/internet-aware-objects) en el Windows SDK para obtener una lista de ejemplo.||

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

##  <a name="required_category"></a>REQUIRED_CATEGORY

Agregue una macro REQUIRED_CATEGORY al [mapa de categorías](#begin_category_map) del componente para especificar que se debe registrar como un requisito de la categoría identificada por el parámetro CATID.

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parámetros

*catID*<br/>
de Una constante CATId o variable que contiene el identificador único global (GUID) para la categoría requerida. Se tomará la dirección de CATID y se agregará a la asignación. Vea la tabla siguiente para obtener una selección de categorías de acciones.

### <a name="remarks"></a>Comentarios

Las categorías de componentes enumeradas en el mapa se registrarán automáticamente cuando el módulo se registre si la clase tiene una macro [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) asociada.

Los clientes pueden usar la información de categoría registrada para la clase con el fin de determinar sus capacidades y requisitos sin tener que crear una instancia del mismo. Por ejemplo, un control puede requerir que un contenedor admita el enlace de datos. El contenedor puede averiguar si tiene las capacidades necesarias para hospedar el control mediante una consulta al administrador de categorías para las categorías requeridas por ese control. Si el contenedor no admite una característica requerida, puede rechazar el hospedaje del objeto COM.

Para obtener más información sobre las categorías de componentes, incluida una lista de ejemplo, vea [¿Qué son las categorías de componentes y cómo funcionan](/windows/win32/com/component-categories-and-how-they-work) en el Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Selección de categorías de acciones

|DESCRIPCIÓN|Símbolo|GUID del registro|
|-----------------|------------|-------------------|
|Safe para scripting|CATID_SafeForScripting|{7DD95801-9882-11CF-9FA9-00AA006C42C4}|
|Safe para la inicialización|CATID_SafeForInitializing|{7DD95802-9882-11CF-9FA9-00AA006C42C4}|
|Contención de sitio de marco simple|CATID_SimpleFrameControl|{157083E0-2368-11cf-87B9-00AA006C8166}|
|enlace de datos simple|CATID_PropertyNotifyControl|{157083E1-2368-11cf-87B9-00AA006C8166}|
|Enlace de datos avanzado|CATID_VBDataBound|{157083E2-2368-11cf-87B9-00AA006C8166}|
|Controles sin ventana|CATID_WindowlessObject|{1D06B600-3AE3-11cf-87B9-00AA006C8166}|
|Objetos que reconocen Internet|Consulte [objetos con reconocimiento de Internet](/windows/win32/com/internet-aware-objects) en el Windows SDK para obtener una lista de ejemplo.||

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
