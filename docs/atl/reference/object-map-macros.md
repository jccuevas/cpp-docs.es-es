---
title: Macros de mapa de objetos
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 73dc924527bac8499adefab3d0d6b51afa500a5a
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/06/2020
ms.locfileid: "78863236"
---
# <a name="object-map-macros"></a>Macros de mapa de objetos

Estas macros definen asignaciones y entradas de objetos.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Permite especificar la descripción de texto de un objeto de clase, que se incluirá en el mapa de objetos.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Especifica un objeto ATL en el mapa de objetos, actualiza el registro y crea una instancia del objeto.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Le permite especificar que el objeto debe estar registrado e inicializado, pero no se debe poder crear externamente que se pueden crear con `CoCreateInstance`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom. h

##  <a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

Permite especificar una descripción de texto para el objeto de clase.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Parámetros

*x*<br/>
de La descripción del objeto de clase.

### <a name="remarks"></a>Observaciones

ATL escribe esta descripción en el mapa de objetos a través de la macro [OBJECT_ENTRY_AUTO](#object_entry_auto) .

DECLARE_OBJECT_DESCRIPTION implementa una función de `GetObjectDescription`, que puede usar para invalidar el método [CComCoClass:: GetObjectDescription](ccomcoclass-class.md#getobjectdescription) .

`IComponentRegistrar::GetComponents`llama a la función `GetObjectDescription`. `IComponentRegistrar` es una interfaz de automatización que permite registrar y anular el registro de componentes individuales en un archivo DLL. Al crear un objeto de registrador de componentes con el Asistente para proyectos ATL, el asistente implementará automáticamente la interfaz `IComponentRegistrar`. Microsoft Transaction Server usa normalmente `IComponentRegistrar`.

Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

Especifica un objeto ATL en el mapa de objetos, actualiza el registro y crea una instancia del objeto.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Parámetros

*CLSID*<br/>
de El CLSID de una clase COM implementada por C++ la clase denominada *Class*.

*class*<br/>
de Nombre de la C++ clase que implementa la clase com representada por *CLSID*.

### <a name="remarks"></a>Observaciones

Las macros de entrada de objeto se colocan en el ámbito global del proyecto para proporcionar compatibilidad con el registro, la inicialización y la creación de una clase.

OBJECT_ENTRY_AUTO escribe los punteros de función de la clase Creator y la clase Creator de generador de clases `CreateInstance` funciones para este objeto en el mapa de objetos ATL generado automáticamente. Cuando se llama a [CAtlComModule:: RegisterServer](catlcommodule-class.md#registerserver) , actualiza el registro del sistema para cada objeto del mapa de objetos.

En la tabla siguiente se describe cómo se obtiene la información agregada al mapa de objetos de la clase proporcionada como segundo parámetro a esta macro.

|Información de|Obtenido de|
|---------------------|-------------------|
|Registro COM|[Macros de Registro](../../atl/reference/registry-macros.md)|
|Creación de un generador de clases|[Macros de generador de clases](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Creación de instancias|[Macros de agregación](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Registro de categoría de componentes|[Macros de categoría](../../atl/reference/category-macros.md)|
|Inicialización y limpieza de nivel de clase|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

##  <a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Le permite especificar que el objeto debe estar registrado e inicializado, pero no se debe poder crear externamente que se pueden crear con `CoCreateInstance`.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Parámetros

*CLSID*<br/>
de El CLSID de una clase COM implementada por C++ la clase denominada *Class*.

*class*<br/>
de Nombre de la C++ clase que implementa la clase com representada por *CLSID*.

### <a name="remarks"></a>Observaciones

Las macros de entrada de objeto se colocan en el ámbito global del proyecto para proporcionar compatibilidad con el registro, la inicialización y la creación de una clase.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO permite especificar que se debe registrar e inicializar un objeto (vea [OBJECT_ENTRY_AUTO](#object_entry_auto) para obtener más información), pero no se debe poder crear a través de `CoCreateInstance`.

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
