---
title: Macros de mapa de objetos
ms.date: 11/04/2016
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
ms.openlocfilehash: 66a418019ba506a5832c8e3ad86a3764c1186df0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326213"
---
# <a name="object-map-macros"></a>Macros de mapa de objetos

Estas macros definen mapas de objetos y entradas.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Le permite especificar la descripción de texto de un objeto de clase, que se introducirá en el mapa de objetos.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Escribe un objeto ATL en el mapa de objetos, actualiza el registro y crea una instancia del objeto.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Le permite especificar que el objeto debe estar registrado e inicializado, pero no se debe poder crear externamente que se pueden crear con `CoCreateInstance`.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

## <a name="declare_object_description"></a><a name="declare_object_description"></a>DECLARE_OBJECT_DESCRIPTION

Le permite especificar una descripción de texto para el objeto de clase.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Parámetros

*X*<br/>
[en] Descripción del objeto de clase.

### <a name="remarks"></a>Observaciones

ATL introduce esta descripción en el mapa de objetos a través de la macro [OBJECT_ENTRY_AUTO.](#object_entry_auto)

DECLARE_OBJECT_DESCRIPTION implementa `GetObjectDescription` una función, que puede usar para invalidar el [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) método.

La `GetObjectDescription` función `IComponentRegistrar::GetComponents`es llamada por . `IComponentRegistrar`es una interfaz de automatización que le permite registrar y anular el registro de componentes individuales en un archivo DLL. Al crear un objeto Deregistrador de componentes con el `IComponentRegistrar` Asistente para proyectos ATL, el asistente implementará automáticamente la interfaz. `IComponentRegistrar`normalmente lo utiliza Microsoft Transaction Server.

Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [Creación de un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

## <a name="object_entry_auto"></a><a name="object_entry_auto"></a>OBJECT_ENTRY_AUTO

Escribe un objeto ATL en el mapa de objetos, actualiza el registro y crea una instancia del objeto.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
[en] El CLSID de una clase COM implementada por la clase C++ denominada *class*.

*clase*<br/>
[en] El nombre de la clase C++ que implementa la clase COM representada por *clsid*.

### <a name="remarks"></a>Observaciones

Las macros de entrada de objeto se colocan en el ámbito global del proyecto para proporcionar compatibilidad con el registro, la inicialización y la creación de una clase.

OBJECT_ENTRY_AUTO entra en los punteros de función de `CreateInstance` las funciones de clase creator y class creator de class-factory para este objeto en el mapa de objetos ATL generado automáticamente. Cuando [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) se llama, actualiza el registro del sistema para cada objeto en el mapa de objetos.

En la tabla siguiente se describe cómo se obtiene la información agregada al mapa de objetos de la clase dada como segundo parámetro de esta macro.

|Información para|Obtenido de|
|---------------------|-------------------|
|Registro COM|[Macros del Registro](../../atl/reference/registry-macros.md)|
|Creación de fábricas de clases|[Macros de fábrica de clases](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Creación de instancias|[Macros de agregación](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Registro de categorías de componentes|[Categoría Macros](../../atl/reference/category-macros.md)|
|Inicialización y limpieza a nivel de clase|[ObjectMain](ccomobjectrootex-class.md#objectmain)|

## <a name="object_entry_non_createable_ex_auto"></a><a name="object_entry_non_createable_ex_auto"></a>OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Le permite especificar que el objeto debe estar registrado e inicializado, pero no se debe poder crear externamente que se pueden crear con `CoCreateInstance`.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Parámetros

*clsid*<br/>
[en] El CLSID de una clase COM implementada por la clase C++ denominada *class*.

*clase*<br/>
[en] El nombre de la clase C++ que implementa la clase COM representada por *clsid*.

### <a name="remarks"></a>Observaciones

Las macros de entrada de objeto se colocan en el ámbito global del proyecto para proporcionar compatibilidad con el registro, la inicialización y la creación de una clase.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO permite especificar que un objeto debe registrarse e inicializarse (consulte [OBJECT_ENTRY_AUTO](#object_entry_auto) para `CoCreateInstance`obtener más información), pero no debe ser creable a través de .

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
