---
title: Macros para plantillas de proveedores OLE DB
ms.date: 02/11/2019
f1_keywords:
- BEGIN_PROPERTY_SET
- BEGIN_PROPERTY_SET_EX
- BEGIN_PROPSET_MAP
- CHAIN_PROPERTY_SET
- END_PROPERTY_SET
- END_PROPSET_MAP
- PROPERTY_INFO_ENTRY
- PROPERTY_INFO_ENTRY_EX
- PROPERTY_INFO_ENTRY_VALUE
- BEGIN_PROVIDER_COLUMN_MAP
- END_PROVIDER_COLUMN_MAP
- PROVIDER_COLUMN_ENTRY
- PROVIDER_COLUMN_ENTRY_FIXED
- PROVIDER_COLUMN_ENTRY_GN
- PROVIDER_COLUMN_ENTRY_LENGTH
- PROVIDER_COLUMN_ENTRY_STR
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
- PROVIDER_COLUMN_ENTRY_WSTR
- BEGIN_SCHEMA_MAP
- END_SCHEMA_MAP
- SCHEMA_ENTRY
helpviewer_keywords:
- OLE DB provider templates, macros
- macros, OLE DB Provider Templates
- Provider Template macros (OLE DB)
- OLE DB Provider Template macros
- BEGIN_PROPERTY_SET macro
- BEGIN_PROPERTY_SET_EX macro
- BEGIN_PROPSET_MAP macro
- CHAIN_PROPERTY_SET macro
- END_PROPERTY_SET macro
- END_PROPSET_MAP macro
- PROPERTY_INFO_ENTRY macro
- PROPERTY_INFO_ENTRY_EX macro
- PROPERTY_INFO_ENTRY_VALUE macro
- BEGIN_PROVIDER_COLUMN_MAP macro
- END_PROVIDER_COLUMN_MAP macro
- PROVIDER_COLUMN_ENTRY macro
- PROVIDER_COLUMN_ENTRY_FIXED macro
- PROVIDER_COLUMN_ENTRY_GN macro
- PROVIDER_COLUMN_ENTRY_LENGTH macro
- PROVIDER_COLUMN_ENTRY_STR macro
- PROVIDER_COLUMN_ENTRY_TYPE_LENGTH macro
- PROVIDER_COLUMN_ENTRY_WSTR macro
- BEGIN_SCHEMA_MAP macro
- END_SCHEMA_MAP macro
- SCHEMA_ENTRY macro
ms.assetid: 909482c5-64ab-4e52-84a9-1c07091db183
ms.openlocfilehash: 5d29b2548102b056a21ebfccb037af3a766788ba
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81369806"
---
# <a name="macros-for-ole-db-provider-templates"></a>Macros para plantillas de proveedores OLE DB

Las macros del proveedor de plantillas OLE DB ofrecen funcionalidad en las siguientes categorías:

## <a name="property-set-map-macros"></a>Macros de mapa de conjunto de propiedades

|||
|-|-|
|[BEGIN_PROPERTY_SET](#begin_property_set)|Marca el principio de un conjunto de propiedades.|
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Marca el principio de un conjunto de propiedades.|
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Marca el principio de un conjunto de propiedades que se puede ocultar o definir fuera del ámbito del proveedor.|
|[CHAIN_PROPERTY_SET](#chain_property_set)|Cadenas grupos de propiedades juntos.|
|[END_PROPERTY_SET](#end_property_set)|Marca el final de un conjunto de propiedades.|
|[END_PROPSET_MAP](#end_propset_map)|Marca el final de un mapa de conjunto de propiedades.|
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Establece una propiedad específica en una propiedad establecida en un valor predeterminado.|
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Establece una propiedad específica en una propiedad establecida en un valor proporcionado por usted. También le permite establecer indicadores y opciones.|
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Establece una propiedad específica en una propiedad establecida en un valor proporcionado por usted.|

## <a name="column-map-macros"></a>Macros de mapa de columnas

|||
|-|-|
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Marca el principio de las entradas de mapa de columna del proveedor.|
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Marca el final de las entradas de mapa de columna del proveedor.|
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Representa una columna específica admitida por el proveedor.|
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Representa una columna específica admitida por el proveedor. Puede especificar el tipo de datos de columna.|
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Representa una columna específica admitida por el proveedor. Puede especificar el tamaño, el tipo de datos, la precisión, la escala y el GUID del conjunto de filas de esquema de la columna.|
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Representa una columna específica admitida por el proveedor. Puede especificar el tamaño de columna.|
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Representa una columna específica admitida por el proveedor. Se supone que el tipo de columna es una cadena.|
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Representa una columna específica admitida por el proveedor. Al igual que PROVIDER_COLUMN_ENTRY_LENGTH, pero también le permite especificar el tipo de datos de la columna, así como el tamaño.|
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Representa una columna específica admitida por el proveedor. Se supone que el tipo de columna es una cadena de caracteres Unicode.|

## <a name="schema-rowset-macros"></a>Macros de conjunto de filas de esquema

|||
|-|-|
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Marca el principio de una asignación de esquema.|
|[END_SCHEMA_MAP](#end_schema_map)|Marca el final de una asignación de esquema.|
|[SCHEMA_ENTRY](#schema_entry)|Asocia un GUID a una clase.|

## <a name="requirements"></a>Requisitos

**Encabezado:** atldb.h

### <a name="begin_property_set"></a><a name="begin_property_set"></a>BEGIN_PROPERTY_SET

Marca el principio de una propiedad establecida en un mapa de conjunto de propiedades.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parámetros

*Guid*<br/>
[en] El GUID de la propiedad.

#### <a name="example"></a>Ejemplo

Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_property_set_ex"></a><a name="begin_property_set_ex"></a>BEGIN_PROPERTY_SET_EX

Marca el principio de una propiedad establecida en un mapa de conjunto de propiedades.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)
```

#### <a name="parameters"></a>Parámetros

*Guid*<br/>
[en] El GUID de la propiedad.

*Banderas*<br/>
[en] UPROPSET_HIDDEN para cualquier conjunto de propiedades que no desea exponer o UPROPSET_PASSTHROUGH para un proveedor que expone propiedades definidas fuera del ámbito del proveedor.

#### <a name="example"></a>Ejemplo

Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_propset_map"></a><a name="begin_propset_map"></a>BEGIN_PROPSET_MAP

Marca el principio de las entradas de mapa del conjunto de propiedades.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_PROPSET_MAP(Class)
```

#### <a name="parameters"></a>Parámetros

*Clase*<br/>
[en] La clase en la que se especifica este conjunto de propiedades. Se puede especificar un conjunto de propiedades en los siguientes objetos OLE DB:

- [Objetos de origen de datos](/previous-versions/windows/desktop/ms721278(v=vs.85))

- [Objetos de sesión](/previous-versions/windows/desktop/ms711572(v=vs.85))

- [Comandos](/previous-versions/windows/desktop/ms724608(v=vs.85))

#### <a name="example"></a>Ejemplo

Aquí está un mapa del conjunto de propiedades de ejemplo:

[!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]

### <a name="chain_property_set"></a><a name="chain_property_set"></a>CHAIN_PROPERTY_SET

Esta macro encadena grupos de propiedades.

#### <a name="syntax"></a>Sintaxis

```cpp
CHAIN_PROPERTY_SET(ChainClass)
```

#### <a name="parameters"></a>Parámetros

*ChainClass*<br/>
[en] El nombre de la clase para la que se va a encadenar propiedades. Se trata de una clase generada por el Asistente para proyectos ATL que ya contiene un mapa (como una sesión, un comando o una clase de objeto de origen de datos).

#### <a name="remarks"></a>Observaciones

Puede encadenar un conjunto de propiedades de otra clase a su propia clase y, a continuación, tener acceso a las propiedades directamente desde la clase.

> [!CAUTION]
> Utilice esta macro con moderación. El uso incorrecto puede provocar que un consumidor produzca un error en las pruebas de conformidad ole DB.

### <a name="end_property_set"></a><a name="end_property_set"></a>END_PROPERTY_SET

Marca el final de un conjunto de propiedades.

#### <a name="syntax"></a>Sintaxis

```cpp
END_PROPERTY_SET(guid)
```

#### <a name="parameters"></a>Parámetros

*Guid*<br/>
[en] El GUID de la propiedad.

#### <a name="example"></a>Ejemplo

Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="end_propset_map"></a><a name="end_propset_map"></a>END_PROPSET_MAP

Marca el final de las entradas de mapa del conjunto de propiedades.

#### <a name="syntax"></a>Sintaxis

```cpp
END_PROPSET_MAP()
```

#### <a name="example"></a>Ejemplo

Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry"></a><a name="property_info_entry"></a>PROPERTY_INFO_ENTRY

Representa una propiedad concreta de un conjunto de propiedades.

#### <a name="syntax"></a>Sintaxis

```cpp
PROPERTY_INFO_ENTRY(dwPropID)
```

#### <a name="parameters"></a>Parámetros

*dwPropID*<br/>
[in] Valor [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) que se puede usar con el GUID del conjunto de propiedades para identificar una propiedad.

#### <a name="remarks"></a>Observaciones

Esta macro establece el valor de propiedad de tipo `DWORD` en un valor predeterminado definido en ATLDB. H. Para establecer la propiedad en un valor de su elección, use [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Para establecer `VARTYPE` [y DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) para la propiedad al mismo tiempo, utilice [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Ejemplo

Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_ex"></a><a name="property_info_entry_ex"></a>PROPERTY_INFO_ENTRY_EX

Representa una propiedad concreta de un conjunto de propiedades.

#### <a name="syntax"></a>Sintaxis

```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)
```

#### <a name="parameters"></a>Parámetros

*dwPropID*<br/>
[in] Valor [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) que se puede usar con el GUID del conjunto de propiedades para identificar una propiedad.

*vt*<br/>
[in] La `VARTYPE` de esta entrada de la propiedad. (Definido en wtypes.h)

*dwFlags*<br/>
[in] Un valor [DBPROPFLAGS](/previous-versions/windows/desktop/ms724342(v=vs.85)) que describe esta entrada de la propiedad.

*value*<br/>
[in] El valor de la propiedad de tipo `DWORD`.

*Opciones*<br/>
DBPROPOPTIONS_REQUIRED o DBPROPOPTIONS_SETIFCHEAP. Normalmente, un proveedor no necesita establecer *opciones* ya que lo establece el consumidor.

#### <a name="remarks"></a>Observaciones

Con esta macro, puede especificar directamente el valor de propiedad de tipo `DWORD` así como opciones y marcas. Para establecer simplemente una propiedad a un valor predeterminado definido en ATLDB.H, use [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Para establecer una propiedad a un valor de su elección, sin establecer opciones ni marcas en ella, use [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).

#### <a name="example"></a>Ejemplo

Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="property_info_entry_value"></a><a name="property_info_entry_value"></a>PROPERTY_INFO_ENTRY_VALUE

Representa una propiedad concreta de un conjunto de propiedades.

#### <a name="syntax"></a>Sintaxis

```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)
```

#### <a name="parameters"></a>Parámetros

*dwPropID*<br/>
[in] Valor [DBPROPID](/previous-versions/windows/desktop/ms723882(v=vs.85)) que se puede usar con el GUID del conjunto de propiedades para identificar una propiedad.

*value*<br/>
[in] El valor de la propiedad de tipo `DWORD`.

#### <a name="remarks"></a>Observaciones

Con esta macro, puede especificar directamente `DWORD`el valor de propiedad de tipo . Para establecer la propiedad en el valor predeterminado definido en ATLDB. H, utilice [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Para establecer el valor, las marcas y las opciones de la propiedad, utilice [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).

#### <a name="example"></a>Ejemplo

Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).

### <a name="begin_provider_column_map"></a><a name="begin_provider_column_map"></a>BEGIN_PROVIDER_COLUMN_MAP

Marca el principio de las entradas de mapa de columna del proveedor.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)
```

#### <a name="parameters"></a>Parámetros

*theClass*<br/>
[en] El nombre de la clase a la que pertenece este mapa.

#### <a name="example"></a>Ejemplo

Aquí está un mapa de columna del proveedor de ejemplo:

[!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]

### <a name="end_provider_column_map"></a><a name="end_provider_column_map"></a>END_PROVIDER_COLUMN_MAP

Marca el final de las entradas de mapa de columna del proveedor.

#### <a name="syntax"></a>Sintaxis

```cpp
END_PROVIDER_COLUMN_MAP()
```

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry"></a><a name="provider_column_entry"></a>PROVIDER_COLUMN_ENTRY

Representa una columna específica admitida por el proveedor.

#### <a name="syntax"></a>Sintaxis

```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
[en] El nombre de la columna.

*Ordinal*<br/>
[en] El número de columna. A menos que la columna sea una columna Bookmark, el número de columna no debe ser 0.

*Miembro*<br/>
[en] La variable `dataClass` miembro correspondiente a la columna.

### <a name="provider_column_entry_fixed"></a><a name="provider_column_entry_fixed"></a>PROVIDER_COLUMN_ENTRY_FIXED

Representa una columna específica admitida por el proveedor.

#### <a name="syntax"></a>Sintaxis

```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
[en] El nombre de la columna.

*Ordinal*<br/>
[en] El número de columna. A menos que la columna sea una columna Bookmark, el número de columna no debe ser 0.

*Dbtype*<br/>
[en] El tipo de datos en [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Miembro*<br/>
[en] La variable `dataClass` miembro que almacena los datos.

#### <a name="remarks"></a>Observaciones

Le permite especificar el tipo de datos de columna.

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_gn"></a><a name="provider_column_entry_gn"></a>PROVIDER_COLUMN_ENTRY_GN

Representa una columna específica admitida por el proveedor.

#### <a name="syntax"></a>Sintaxis

```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
[en] El nombre de la columna.

*Ordinal*<br/>
[en] El número de columna. A menos que la columna sea una columna Bookmark, el número de columna no debe ser 0.

*Banderas*<br/>
[en] Especifica cómo se devuelven los datos. Consulte `dwFlags` la descripción en [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*colSize*<br/>
[en] El tamaño de la columna.

*Dbtype*<br/>
[en] Indica el tipo de datos del valor. Consulte `wType` la descripción en [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Precisión*<br/>
[en] Indica la precisión que se debe utilizar al obtener datos si *dbType* está DBTYPE_NUMERIC o DBTYPE_DECIMAL. Consulte `bPrecision` la descripción en [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Escala*<br/>
[en] Indica la escala que se usará al obtener datos si dbType es DBTYPE_NUMERIC o DBTYPE_DECIMAL. Consulte `bScale` la descripción en [DBBINDING Structures](/previous-versions/windows/desktop/ms716845(v=vs.85)).

*Guid*<br/>
Guid de conjunto de filas de esquema. Consulte [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) en la *referencia del programador OLE DB* para obtener una lista de conjuntos de filas de esquema y sus GUID.

#### <a name="remarks"></a>Observaciones

Le permite especificar el tamaño, el tipo de datos, la precisión, la escala y el GUID del conjunto de filas de esquema de la columna.

### <a name="provider_column_entry_length"></a><a name="provider_column_entry_length"></a>PROVIDER_COLUMN_ENTRY_LENGTH

Representa una columna específica admitida por el proveedor.

#### <a name="syntax"></a>Sintaxis

```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
[en] El nombre de la columna.

*Ordinal*<br/>
[en] El número de columna. A menos que la columna sea una columna Bookmark, el número de columna no debe ser 0.

*Tamaño*<br/>
[en] El tamaño de columna en bytes.

*Miembro*<br/>
[en] La variable `dataClass` miembro que almacena los datos de columna.

#### <a name="remarks"></a>Observaciones

Le permite especificar el tamaño de columna.

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_str"></a><a name="provider_column_entry_str"></a>PROVIDER_COLUMN_ENTRY_STR

Representa una columna específica admitida por el proveedor.

#### <a name="syntax"></a>Sintaxis

```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
[en] El nombre de la columna.

*Ordinal*<br/>
[en] El número de columna. A menos que la columna sea una columna Bookmark, el número de columna no debe ser 0.

*Miembro*<br/>
[en] La variable miembro de la clase de datos que almacena los datos.

#### <a name="remarks"></a>Observaciones

Utilice esta macro cuando se supone que los datos de columna son [DBTYPE_STR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

#### <a name="example"></a>Ejemplo

Consulte [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).

### <a name="provider_column_entry_type_length"></a><a name="provider_column_entry_type_length"></a>PROVIDER_COLUMN_ENTRY_TYPE_LENGTH

Representa una columna específica admitida por el proveedor.

#### <a name="syntax"></a>Sintaxis

```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
[en] El nombre de la columna.

*Ordinal*<br/>
[en] El número de columna. A menos que la columna sea una columna Bookmark, el número de columna no debe ser 0.

*Dbtype*<br/>
[en] El tipo de datos en [DBTYPE](/previous-versions/windows/desktop/ms711251(v=vs.85)).

*Tamaño*<br/>
[en] El tamaño de columna en bytes.

*Miembro*<br/>
[en] La variable miembro de la clase de datos que almacena los datos.

#### <a name="remarks"></a>Observaciones

Similar a [PROVIDER_COLUMN_ENTRY_LENGTH,](../../data/oledb/provider-column-entry-length.md) pero también le permite especificar el tipo de datos de la columna, así como el tamaño.

### <a name="provider_column_entry_wstr"></a><a name="provider_column_entry_wstr"></a>PROVIDER_COLUMN_ENTRY_WSTR

Representa una columna específica admitida por el proveedor.

#### <a name="syntax"></a>Sintaxis

```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)
```

#### <a name="parameters"></a>Parámetros

*name*<br/>
[en] El nombre de la columna.

*Ordinal*<br/>
[en] El número de columna. A menos que la columna sea una columna Bookmark, el número de columna no debe ser 0.

*Miembro*<br/>
[en] La variable miembro de la clase de datos que almacena los datos.

#### <a name="remarks"></a>Observaciones

Utilice esta macro cuando los datos de columna sean una cadena de caracteres Unicode terminada en null, [DBTYPE_WSTR](/previous-versions/windows/desktop/ms711251(v=vs.85)).

### <a name="begin_schema_map"></a><a name="begin_schema_map"></a>BEGIN_SCHEMA_MAP

Indica el principio de una asignación de esquema.

#### <a name="syntax"></a>Sintaxis

```cpp
BEGIN_SCHEMA_MAP(SchemaClass);
```

#### <a name="parameters"></a>Parámetros

*SchemaClass*<br/>
La clase que contiene el MAP. Normalmente, esta será la clase de sesión.

#### <a name="remarks"></a>Observaciones

Consulte [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) en el Windows SDK para obtener más información acerca de los conjuntos de filas de esquema.

### <a name="end_schema_map"></a><a name="end_schema_map"></a>END_SCHEMA_MAP

Indica el final de la asignación de esquema.

#### <a name="syntax"></a>Sintaxis

```cpp
END_SCHEMA_MAP()
```

#### <a name="remarks"></a>Observaciones

Para obtener más información, vea [IDBSchemaRowsetImpl (Clase)](../../data/oledb/idbschemarowsetimpl-class.md).

### <a name="schema_entry"></a><a name="schema_entry"></a>SCHEMA_ENTRY

Asocia un GUID a una clase.

#### <a name="syntax"></a>Sintaxis

```cpp
SCHEMA_ENTRY(guid,
   rowsetClass);
```

#### <a name="parameters"></a>Parámetros

*Guid*<br/>
Guid de conjunto de filas de esquema. Consulte [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) en la *referencia del programador OLE DB* para obtener una lista de conjuntos de filas de esquema y sus GUID.

*rowsetClass*<br/>
La clase que se creará para representar el conjunto de filas de esquema.

#### <a name="remarks"></a>Observaciones

[IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) puede, a continuación, consultar la asignación para obtener una lista de GUID, o puede crear un conjunto de filas si se le da un GUID. El conjunto `IDBSchemaRowsetImpl` de filas de `CRowsetImpl`esquema crea es similar a `Execute` una clase derivada estándar, excepto que debe proporcionar un método que tenga la siguiente firma:

```cpp
HRESULT Execute (LONG* pcRowsAffected,
    ULONG cRestrictions,
    const VARIANT* rgRestrictions);
```

Esta `Execute` función rellena los datos del conjunto de filas. El Asistente para proyectos ATL crea, como se describe en [IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85)) en la *referencia del programador OLE DB*, tres conjuntos de filas de esquema iniciales en el proyecto para cada uno de los tres esquemas OLE DB obligatorios:

- DBSCHEMA_TABLES

- DBSCHEMA_COLUMNS

- DBSCHEMA_PROVIDER_TYPES

El asistente también agrega tres entradas correspondientes en el mapa de esquema. Consulte [Creación de un proveedor](../../data/oledb/creating-an-ole-db-provider.md) de plantillas OLE DB para obtener más información sobre el uso del asistente para crear un proveedor.

## <a name="see-also"></a>Consulte también

[Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)<br/>
[Arquitectura de plantillas de proveedor OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
[Creación de un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
[Referencia de plantillas de proveedor OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)<br/>
[Macros para plantillas de proveedor OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)
