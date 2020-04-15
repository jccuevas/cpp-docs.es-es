---
title: Macros de objetos de conexión
ms.date: 11/04/2016
f1_keywords:
- atlsnap/ATL::BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::BEGIN_SNAPINTOOLBARID_MAP
- atlsnap/ATL::END_EXTENSION_SNAPIN_NODEINFO_MAP
- atlsnap/ATL::END_SNAPINTOOLBARID_MAP
- atlsnap/ATL::EXTENSION_SNAPIN_DATACLASS
- atlsnap/ATL::EXTENSION_SNAPIN_NODEINFO_ENTRY
- atlsnap/ATL::SNAPINMENUID
- atlsnap/ATL::SNAPINTOOLBARID_ENTRY
ms.assetid: 4e9850c0-e395-4929-86c9-584a81828053
ms.openlocfilehash: 6a57cdb3c9b6a4448bc954ff754ac9b18fa0b393
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81325857"
---
# <a name="snap-in-object-macros"></a>Macros de objetos de conexión

Estas macros proporcionan compatibilidad con extensiones de complemento.

|||
|-|-|
|[BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map)|Marca el principio del mapa de clase de datos de extensión de complemento para un objeto Snap-In.|
|[BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map)|Marca el principio del mapa de la barra de herramientas para un objeto Snap-In.|
|[END_EXTENSION_SNAPIN_NODEINFO_MAP](#end_extension_snapin_nodeinfo_map)|Marca el final del mapa de clase de datos de extensión de complemento para un objeto Snap-In.|
|[END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map)|Marca el final del mapa de la barra de herramientas para un objeto Snap-In.|
|[EXTENSION_SNAPIN_DATACLASS](#extension_snapin_dataclass)|Crea un miembro de datos para la clase de datos de la extensión de complemento.|
|[EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry)|Escribe una clase de datos de extensión de complemento en el mapa de clase de datos de extensión de complemento del objeto Snap-In.|
|[SNAPINMENUID](#snapinmenuid)|Declara el identificador del menú contextual utilizado por el objeto Snap-In.|
|[SNAPINTOOLBARID_ENTRY](#snapintoolbarid_entry)|Introduce una barra de herramientas en el mapa de la barra de herramientas del objeto Snap-In.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atlsnap.h

## <a name="begin_extension_snapin_nodeinfo_map"></a><a name="begin_extension_snapin_nodeinfo_map"></a>BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP

Marca el principio del mapa de clases de datos de extensión de complemento.

```
BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP(classname)
```

### <a name="parameters"></a>Parámetros

*Classname*<br/>
[en] El nombre de la clase de datos de extensión de complemento.

### <a name="remarks"></a>Observaciones

Inicie el mapa de extensión de complemento con la macro BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP, agregue entradas para cada uno de los tipos de datos de extensión de complemento con la macro [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) y complete el mapa con la macro [END_EXTENSION_SNAPIN_NODEINFO_MAP.](#end_extension_snapin_nodeinfo_map)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="begin_snapintoolbarid_map"></a><a name="begin_snapintoolbarid_map"></a>BEGIN_SNAPINTOOLBARID_MAP

Declara el principio del mapa de ID de barra de herramientas para el objeto Snap-In.

```
BEGIN_SNAPINTOOLBARID_MAP(_class)
```

### <a name="parameters"></a>Parámetros

*_class*<br/>
[en] Especifica la clase de objeto Snap-In.

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#106](../../atl/codesnippet/cpp/snap-in-object-macros_2.h)]

## <a name="end_extension_snapin_nodeinfo_map"></a><a name="end_extension_snapin_nodeinfo_map"></a>END_EXTENSION_SNAPIN_NODEINFO_MAP

Marca el final del mapa de clase de datos de extensión de complemento.

```
END_EXTENSION_SNAPIN_NODEINFO_MAP()
```

### <a name="remarks"></a>Observaciones

Inicie el mapa de extensión de complemento con la macro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP,](#begin_extension_snapin_nodeinfo_map) agregue entradas para cada uno de los tipos de datos de complemento de extensión con la macro [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) y complete el mapa con la macro END_EXTENSION_SNAPIN_NODEINFO_MAP.

### <a name="example"></a>Ejemplo

Consulte el ejemplo [de BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="end_snapintoolbarid_map"></a><a name="end_snapintoolbarid_map"></a>END_SNAPINTOOLBARID_MAP

Declara el final del mapa de ID de barra de herramientas para el objeto Snap-In.

```
END_SNAPINTOOLBARID_MAP( _class )
```

### <a name="parameters"></a>Parámetros

*_class*<br/>
[en] Especifica la clase de objeto Snap-In.

### <a name="example"></a>Ejemplo

Consulte el ejemplo de [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="extension_snapin_dataclass"></a><a name="extension_snapin_dataclass"></a>EXTENSION_SNAPIN_DATACLASS

Agrega un miembro de datos a la clase de datos de extensión de complemento para una clase derivada **de ISnapInItemImpl.**

```
EXTENSION_SNAPIN_DATACLASS(dataClass )
```

### <a name="parameters"></a>Parámetros

*dataClass*<br/>
[en] La clase de datos de la extensión de complemento.

### <a name="remarks"></a>Observaciones

Esta clase también debe escribirse en un mapa de clase de datos de extensión de complemento. Inicie el mapa de clase de datos de extensión de complemento con la macro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP,](#begin_extension_snapin_nodeinfo_map) agregue entradas para cada uno de los tipos de datos de extensión de complemento con la macro [EXTENSION_SNAPIN_NODEINFO_ENTRY](#extension_snapin_nodeinfo_entry) y complete el mapa con la macro [END_EXTENSION_SNAPIN_NODEINFO_MAP.](#end_extension_snapin_nodeinfo_map)

### <a name="example"></a>Ejemplo

[!code-cpp[NVC_ATL_Windowing#105](../../atl/codesnippet/cpp/snap-in-object-macros_1.h)]

## <a name="extension_snapin_nodeinfo_entry"></a><a name="extension_snapin_nodeinfo_entry"></a>EXTENSION_SNAPIN_NODEINFO_ENTRY

Agrega una clase de datos de extensión de complemento al mapa de clase de datos de extensión de complemento.

```
EXTENSION_SNAPIN_NODEINFO_ENTRY( dataClass )
```

### <a name="parameters"></a>Parámetros

*dataClass*<br/>
[en] La clase de datos de la extensión de complemento.

### <a name="remarks"></a>Observaciones

Inicie el mapa de clase de datos de extensión de complemento con la macro [BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP,](#begin_extension_snapin_nodeinfo_map) agregue entradas para cada uno de los tipos de datos de extensión de complemento con la macro EXTENSION_SNAPIN_NODEINFO_ENTRY y complete el mapa con la macro [END_EXTENSION_SNAPIN_NODEINFO_MAP.](#end_extension_snapin_nodeinfo_map)

### <a name="example"></a>Ejemplo

Consulte el ejemplo [de BEGIN_EXTENSION_SNAPIN_NODEINFO_MAP](#begin_extension_snapin_nodeinfo_map).

## <a name="snapinmenuid"></a><a name="snapinmenuid"></a>SNAPINMENUID

Utilice esta macro para declarar el recurso de menú contextual del objeto Snap-In.

```
SNAPINMENUID( id )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identifica el menú contextual del objeto Snap-In.

## <a name="snapintoolbarid_entry"></a><a name="snapintoolbarid_entry"></a>SNAPINTOOLBARID_ENTRY

Utilice esta macro para introducir un ID de barra de herramientas en el mapa de ID de barra de herramientas del objeto Snap-In.

```
SNAPINTOOLBARID_ENTRY( id )
```

### <a name="parameters"></a>Parámetros

*id*<br/>
[en] Identifica el control de barra de herramientas.

### <a name="remarks"></a>Observaciones

La macro [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map) marca el principio del mapa de ID de la barra de herramientas; la macro [END_SNAPINTOOLBARID_MAP](#end_snapintoolbarid_map) marca el final.

### <a name="example"></a>Ejemplo

Consulte el ejemplo de [BEGIN_SNAPINTOOLBARID_MAP](#begin_snapintoolbarid_map).

## <a name="see-also"></a>Consulte también

[Macros](../../atl/reference/atl-macros.md)
