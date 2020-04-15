---
title: Categoría Macros
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::BEGIN_CATEGORY_MAP
- atlcom/ATL::END_CATEGORY_MAP
- atlcom/ATL::IMPLEMENTED_CATEGORY
- atlcom/ATL::REQUIRED_CATEGORY
ms.assetid: 223578cb-6180-4787-a8d8-ba3787a5d3ee
ms.openlocfilehash: 1d8bbae4608aa661bbc612604f7d85855f325f5f
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81321596"
---
# <a name="category-macros"></a>Categoría Macros

Estas macros definen mapas de categorías.

|||
|-|-|
|[BEGIN_CATEGORY_MAP](#begin_category_map)|Marca el principio del mapa de categorías.|
|[END_CATEGORY_MAP](#end_category_map)|Marca el final del mapa de categorías.|
|[IMPLEMENTED_CATEGORY](#implemented_category)|Indica las categorías implementadas por el objeto COM.|
|[REQUIRED_CATEGORY](#required_category)|Indica las categorías que el objeto COM requiere del contenedor.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="begin_category_map"></a><a name="begin_category_map"></a>BEGIN_CATEGORY_MAP

Marca el principio del mapa de categorías.

```
BEGIN_CATEGORY_MAP(theClass)
```

### <a name="parameters"></a>Parámetros

*theClass*<br/>
[en] El nombre de la clase que contiene el mapa de categorías.

### <a name="remarks"></a>Observaciones

El mapa de categorías se utiliza para especificar qué categorías de componentes implementará la clase COM y qué categorías requiere de su contenedor.

Agregue una [entrada IMPLEMENTED_CATEGORY](#implemented_category) al mapa para cada categoría implementada por la clase COM. Agregue una [entrada REQUIRED_CATEGORY](#required_category) al mapa para cada categoría que la clase requiere que sus clientes implementen. Marque el final del mapa con la macro [END_CATEGORY_MAP.](#end_category_map)

Las categorías de componentes enumeradas en el mapa se registrarán automáticamente cuando se registre el módulo si la clase tiene un [OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto)asociado.

> [!NOTE]
> ATL utiliza el administrador de categorías de componentes estándar para registrar categorías de componentes. Si el administrador no está presente en el sistema cuando se registra el módulo, el registro se realiza correctamente, pero las categorías de componentes no se registrarán para esa clase.

Para obtener más información acerca de las categorías de componentes, vea [Qué son las categorías](/windows/win32/com/component-categories-and-how-they-work) de componentes y cómo funcionan en el Windows SDK.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="end_category_map"></a><a name="end_category_map"></a>END_CATEGORY_MAP

Marca el final del mapa de categorías.

```
END_CATEGORY_MAP()
```

### <a name="example"></a>Ejemplo

Consulte el ejemplo [de BEGIN_CATEGORY_MAP](#begin_category_map).

## <a name="implemented_category"></a><a name="implemented_category"></a>IMPLEMENTED_CATEGORY

Agregue una macro de IMPLEMENTED_CATEGORY al mapa de [categorías](#begin_category_map) del componente para especificar que se debe registrar como la implementación de la categoría identificada por el parámetro *catID.*

```
IMPLEMENTED_CATEGORY(catID)
```

### <a name="parameters"></a>Parámetros

*catID*<br/>
[en] Una constante o variable CATID que contiene el identificador único global (GUID) para la categoría implementada. La dirección de *catID* se tomará y se agregará al mapa. Consulte la tabla siguiente para ver una selección de categorías de stock.

### <a name="remarks"></a>Observaciones

Las categorías de componentes enumeradas en el mapa se registrarán automáticamente cuando se registre el módulo si la clase tiene una [macro OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) asociada.

Los clientes pueden usar la información de categoría registrada para la clase para determinar sus capacidades y requisitos sin tener que crear una instancia de ella.

Para obtener más información acerca de las categorías de componentes, vea [Qué son las categorías](/windows/win32/com/component-categories-and-how-they-work) de componentes y cómo funcionan en el Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Una selección de categorías de acciones

|Descripción|Símbolo|GUID del registro|
|-----------------|------------|-------------------|
|Seguro para scripting|CATID_SafeForScripting|N.o 7DD95801-9882-11CF-9FA9-00AA006C42C4|
|Seguro para la inicialización|CATID_SafeForInitializing|N.o 7DD95802-9882-11CF-9FA9-00AA006C42C4|
|Contención de sitios de marco simple|CATID_SimpleFrameControl|N.o 157083E0-2368-11cf-87B9-00AA006C8166|
|enlace de datos simple|CATID_PropertyNotifyControl|N.o 157083E1-2368-11cf-87B9-00AA006C8166|
|Enlace de datos avanzado|CATID_VBDataBound|N.o 157083E2-2368-11cf-87B9-00AA006C8166|
|Controles sin ventana|CATID_WindowlessObject|N.o 1D06B600-3AE3-11cf-87B9-00AA006C8166|
|Objetos compatibles con Internet|Consulte [Objetos compatibles con Internet](/windows/win32/com/internet-aware-objects) en el Windows SDK para obtener una lista de ejemplo.||

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#100](../../atl/codesnippet/cpp/category-macros_1.h)]

## <a name="required_category"></a><a name="required_category"></a>REQUIRED_CATEGORY

Agregue una macro REQUIRED_CATEGORY al mapa de [categorías](#begin_category_map) del componente para especificar que debe registrarse como que requiere la categoría identificada por el parámetro *catID.*

```
REQUIRED_CATEGORY( catID )
```

### <a name="parameters"></a>Parámetros

*catID*<br/>
[en] Una constante o variable CATID que contiene el identificador único global (GUID) para la categoría necesaria. La dirección de *catID* se tomará y se agregará al mapa. Consulte la tabla siguiente para ver una selección de categorías de stock.

### <a name="remarks"></a>Observaciones

Las categorías de componentes enumeradas en el mapa se registrarán automáticamente cuando se registre el módulo si la clase tiene una [macro OBJECT_ENTRY_AUTO](../../atl/reference/object-map-macros.md#object_entry_auto) o [OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](../../atl/reference/object-map-macros.md#object_entry_non_createable_ex_auto) asociada.

Los clientes pueden usar la información de categoría registrada para la clase para determinar sus capacidades y requisitos sin tener que crear una instancia de ella. Por ejemplo, un control puede requerir que un contenedor admita el enlace de datos. El contenedor puede averiguar si tiene las capacidades necesarias para hospedar el control consultando al administrador de categorías para las categorías requeridas por ese control. Si el contenedor no admite una característica necesaria, puede negarse a hospedar el objeto COM.

Para obtener más información acerca de las categorías de componentes, incluida una lista de ejemplo, vea [Qué son las categorías](/windows/win32/com/component-categories-and-how-they-work) de componentes y cómo funcionan en el Windows SDK.

### <a name="a-selection-of-stock-categories"></a>Una selección de categorías de acciones

|Descripción|Símbolo|GUID del registro|
|-----------------|------------|-------------------|
|Seguro para scripting|CATID_SafeForScripting|N.o 7DD95801-9882-11CF-9FA9-00AA006C42C4|
|Seguro para la inicialización|CATID_SafeForInitializing|N.o 7DD95802-9882-11CF-9FA9-00AA006C42C4|
|Contención de sitios de marco simple|CATID_SimpleFrameControl|N.o 157083E0-2368-11cf-87B9-00AA006C8166|
|enlace de datos simple|CATID_PropertyNotifyControl|N.o 157083E1-2368-11cf-87B9-00AA006C8166|
|Enlace de datos avanzado|CATID_VBDataBound|N.o 157083E2-2368-11cf-87B9-00AA006C8166|
|Controles sin ventana|CATID_WindowlessObject|N.o 1D06B600-3AE3-11cf-87B9-00AA006C8166|
|Objetos compatibles con Internet|Consulte [Objetos compatibles con Internet](/windows/win32/com/internet-aware-objects) en el Windows SDK para obtener una lista de ejemplo.||

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#135](../../atl/codesnippet/cpp/category-macros_2.h)]

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
