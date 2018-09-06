---
title: Objeto Map Macros | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-atl
ms.topic: reference
f1_keywords:
- atlcom/ATL::DECLARE_OBJECT_DESCRIPTION
- atlcom/ATL::OBJECT_ENTRY_AUTO
- atlcom/ATL::OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO
dev_langs:
- C++
ms.assetid: 680087f4-9894-41dd-a79c-6f337e1f13c1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 1061b105b7fd1e344223da3850275910c164774b
ms.sourcegitcommit: 92dbc4b9bf82fda96da80846c9cfcdba524035af
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/05/2018
ms.locfileid: "43761857"
---
# <a name="object-map-macros"></a>Macros de mapa de objetos

Estas macros definen asignaciones de objeto y las entradas.

|||
|-|-|
|[DECLARE_OBJECT_DESCRIPTION](#declare_object_description)|Permite especificar la descripción del texto de un objeto de clase, que se escribirá en el mapa de objetos.|
|[OBJECT_ENTRY_AUTO](#object_entry_auto)|Escribe un objeto ATL en el mapa de objetos, actualiza el registro y crea una instancia del objeto.|
|[OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO](#object_entry_non_createable_ex_auto)|Le permite especificar que el objeto debe estar registrado e inicializado, pero no se debe poder crear externamente que se pueden crear con `CoCreateInstance`.|  

## <a name="requirements"></a>Requisitos

**Encabezado:** atlcom.h

##  <a name="declare_object_description"></a>  DECLARE_OBJECT_DESCRIPTION

Le permite especificar una descripción de texto para el objeto class.

```
DECLARE_OBJECT_DESCRIPTION( x )
```

### <a name="parameters"></a>Parámetros

*x*  
[in] Descripción del objeto de clase.

### <a name="remarks"></a>Comentarios

ATL escribe esta descripción en el mapa de objetos a través de la [OBJECT_ENTRY_AUTO](#object_entry_auto) macro.

DECLARE_OBJECT_DESCRIPTION implementa un `GetObjectDescription` función, que puede usar para invalidar el [CComCoClass::GetObjectDescription](ccomcoclass-class.md#getobjectdescription) método.  

El `GetObjectDescription` llama a la función `IComponentRegistrar::GetComponents`. `IComponentRegistrar` es una interfaz de automatización que le permite registrar y anular el registro de componentes individuales en un archivo DLL. Cuando se crea un objeto de registrador de componentes con el Asistente para proyectos ATL, el Asistente implementará automáticamente la `IComponentRegistrar` interfaz. `IComponentRegistrar` se utiliza normalmente con Microsoft Transaction Server.

Para obtener más información sobre el Asistente para proyectos ATL, vea el artículo [crear un proyecto ATL](../../atl/reference/creating-an-atl-project.md).

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#123](../../atl/codesnippet/cpp/object-map-macros_1.h)]

##  <a name="object_entry_auto"></a>  OBJECT_ENTRY_AUTO

Escribe un objeto ATL en el mapa de objetos, actualiza el registro y crea una instancia del objeto.

```
OBJECT_ENTRY_AUTO( clsid, class )
```

### <a name="parameters"></a>Parámetros

*CLSID*  
[in] El CLSID de una clase COM implementada por la clase de C++ denominada *clase*.

*class*  
[in] El nombre de la clase de C++ que implementa la clase COM representada por *clsid*.

### <a name="remarks"></a>Comentarios

Las macros de entrada de objeto se colocan en el ámbito global del proyecto para proporcionar compatibilidad con el registro, la inicialización y la creación de una clase.

OBJECT_ENTRY_AUTO entra en los punteros de función de la clase de creador y la clase de generador de clases creador `CreateInstance` las funciones de este objeto en el mapa de objetos ATL generado automáticamente. Cuando [CAtlComModule::RegisterServer](catlcommodule-class.md#registerserver) es llamado, actualiza el registro del sistema para cada objeto de mapa de objetos.  

En la tabla siguiente se describe cómo se obtiene la información que se hayan agregado al mapa de objetos de la clase que se proporcionó como el segundo parámetro para esta macro.

|Información de|Obtenida|
|---------------------|-------------------|
|Registro de COM|[Macros de Registro](../../atl/reference/registry-macros.md)|
|Creación del generador de clases|[Macros de clase de fábrica](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Creación de instancias|[Aggregation (Macros)](../../atl/reference/aggregation-and-class-factory-macros.md)|
|Registro de la categoría de componentes|[Macros de categoría](../../atl/reference/category-macros.md)|
|Nivel de clase de inicialización y limpieza|[ObjectMain](ccomobjectrootex-class.md#objectmain)|  

##  <a name="object_entry_non_createable_ex_auto"></a>  OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO

Le permite especificar que el objeto debe estar registrado e inicializado, pero no se debe poder crear externamente que se pueden crear con `CoCreateInstance`.

```
OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO( clsid, class )
```

### <a name="parameters"></a>Parámetros

*CLSID*  
[in] El CLSID de una clase COM implementada por la clase de C++ denominada *clase*.

*class*  
[in] El nombre de la clase de C++ que implementa la clase COM representada por *clsid*.

### <a name="remarks"></a>Comentarios

Las macros de entrada de objeto se colocan en el ámbito global del proyecto para proporcionar compatibilidad con el registro, la inicialización y la creación de una clase.

OBJECT_ENTRY_NON_CREATEABLE_EX_AUTO le permite especificar que un objeto debe estar registrado e inicializado (consulte [OBJECT_ENTRY_AUTO](#object_entry_auto) para obtener más información), pero no debería ser que se pueden crear a través de `CoCreateInstance`.

## <a name="see-also"></a>Vea también

[Macros](../../atl/reference/atl-macros.md)
