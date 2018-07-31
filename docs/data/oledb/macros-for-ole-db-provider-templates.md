---
title: Macros para plantillas de proveedores OLE DB | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- vc.templates.ole
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
dev_langs:
- C++
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a5c9132325af7c05980aac0d7b6b7d53958e4a2b
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39338049"
---
# <a name="macros-for-ole-db-provider-templates"></a>Macros para plantillas de proveedores OLE DB
Las macros de plantillas del proveedor OLE DB proporcionan funcionalidad en las siguientes categorías:  
  
## <a name="property-set-map-macros"></a>Macros de mapa de conjunto de propiedades  
  
|||  
|-|-|  
|[BEGIN_PROPERTY_SET](#begin_property_set)|Marca el principio de un conjunto de propiedades.|  
|[BEGIN_PROPERTY_SET_EX](#begin_property_set_ex)|Marca el principio de un conjunto de propiedades.|  
|[BEGIN_PROPSET_MAP](#begin_propset_map)|Marca que el principio de una propiedad de conjunto que se puede ocultar o definido fuera del ámbito del proveedor.|  
|[CHAIN_PROPERTY_SET](#chain_property_set)|Encadena grupos de propiedades.|  
|[END_PROPERTY_SET](#end_property_set)|Marca el final de un conjunto de propiedades.|  
|[END_PROPSET_MAP](#end_propset_map)|Marca el final de una asignación de conjunto de propiedades.|  
|[PROPERTY_INFO_ENTRY](#property_info_entry)|Establece una propiedad específica en una propiedad establecida en un valor predeterminado.|  
|[PROPERTY_INFO_ENTRY_EX](#property_info_entry_ex)|Establece una propiedad específica en una propiedad establecida en un valor proporcionado por el usuario. También permite establecer las opciones y marcas.|  
|[PROPERTY_INFO_ENTRY_VALUE](#property_info_entry_value)|Establece una propiedad específica en una propiedad establecida en un valor proporcionado por el usuario.|  
  
## <a name="column-map-macros"></a>Macros de mapa de columna  
  
|||  
|-|-|  
|[BEGIN_PROVIDER_COLUMN_MAP](#begin_provider_column_map)|Marca el principio de las entradas de asignación de columna de proveedor.|  
|[END_PROVIDER_COLUMN_MAP](#end_provider_column_map)|Marca el final de las entradas de asignación de columna de proveedor.|  
|[PROVIDER_COLUMN_ENTRY](#provider_column_entry)|Representa una columna específica admitida por el proveedor.|  
|[PROVIDER_COLUMN_ENTRY_FIXED](#provider_column_entry_fixed)|Representa una columna específica admitida por el proveedor. Puede especificar el tipo de datos de columna.|  
|[PROVIDER_COLUMN_ENTRY_GN](#provider_column_entry_gn)|Representa una columna específica admitida por el proveedor. Puede especificar el tamaño de la columna, tipo de datos, precisión, escala y GUID del conjunto de filas de esquema.|  
|[PROVIDER_COLUMN_ENTRY_LENGTH](#provider_column_entry_length)|Representa una columna específica admitida por el proveedor. Puede especificar el tamaño de columna.|  
|[PROVIDER_COLUMN_ENTRY_STR](#provider_column_entry_str)|Representa una columna específica admitida por el proveedor. Se supone que el tipo de columna es una cadena.|  
|[PROVIDER_COLUMN_ENTRY_TYPE_LENGTH](#provider_column_entry_type_length)|Representa una columna específica admitida por el proveedor. Al igual que PROVIDER_COLUMN_ENTRY_LENGTH, pero también permite especificar el tipo de datos de la columna, así como el tamaño.|  
|[PROVIDER_COLUMN_ENTRY_WSTR](#provider_column_entry_wstr)|Representa una columna específica admitida por el proveedor. Se supone que el tipo de columna es una cadena de caracteres Unicode.|  
  
## <a name="schema-rowset-macros"></a>Macros de conjunto de filas de esquema  
  
|||  
|-|-|  
|[BEGIN_SCHEMA_MAP](#begin_schema_map)|Marca el principio de una asignación de esquema.|  
|[END_SCHEMA_MAP](#end_schema_map)|Marca el final de una asignación de esquema.|  
|[SCHEMA_ENTRY](#schema_entry)|Asocia un GUID a una clase.|  

## <a name="requirements"></a>Requisitos  
 **Encabezado:** atldb.h  

### <a name="begin_property_set"></a> BEGIN_PROPERTY_SET
Mapa de definición de marcas de que comienzo de una propiedad establecida en una propiedad.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
BEGIN_PROPERTY_SET(guid)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *GUID*  
 [in] La propiedad GUID.  
  
#### <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="begin_property_set_ex"></a> BEGIN_PROPERTY_SET_EX
Mapa de definición de marcas de que comienzo de una propiedad establecida en una propiedad.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
BEGIN_PROPERTY_SET_EX(guid, flags)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *GUID*  
 [in] La propiedad GUID.  
  
 *flags*  
 [in] UPROPSET_HIDDEN para los conjuntos de propiedades que no desea exponer o UPROPSET_PASSTHROUGH para un proveedor de exponer las propiedades definidas fuera del ámbito del proveedor.  
  
#### <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="begin_propset_map"></a> BEGIN_PROPSET_MAP
Las marcas de comienzo de la propiedad establece entradas de mapa.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
BEGIN_PROPSET_MAP(Class)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *Clase*  
 [in] La clase en el que se especifica esta propiedad establecida. En los siguientes objetos de OLE DB, se puede especificar un conjunto de propiedades:  
  
-   [Objetos de origen de datos](https://msdn.microsoft.com/library/ms721278.aspx)  
  
-   [Objetos de sesión](https://msdn.microsoft.com/library/ms711572.aspx)  
  
-   [Comandos](https://msdn.microsoft.com/library/ms724608.aspx)  
  
#### <a name="example"></a>Ejemplo  
 Este es un mapa de conjunto de propiedades de ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Provider#3](../../data/oledb/codesnippet/cpp/begin-propset-map_1.h)]  

### <a name="chain_property_set"></a> CHAIN_PROPERTY_SET
Esta macro encadena grupos de propiedades.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
CHAIN_PROPERTY_SET(ChainClass)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *ChainClass*  
 [in] El nombre de la clase a las propiedades de cadena para. Se trata de una clase generada por el Asistente para proyectos de ATL que ya contiene un mapa (por ejemplo, una clase de objeto origen de datos, comando o sesión).  
  
#### <a name="remarks"></a>Comentarios  
 Puede encadenar un conjunto de propiedades de otra clase a su propia clase y luego acceder a las propiedades directamente desde la clase.  
  
> [!CAUTION]
>  Use esta macro con moderación. Uso incorrecto puede provocar un consumidor de un error en las pruebas de conformidad de OLE DB.  

### <a name="end_property_set"></a> END_PROPERTY_SET
Marca el final de un conjunto de propiedades.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
END_PROPERTY_SET(guid)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *GUID*  
 [in] La propiedad GUID.  
  
#### <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="end_propset_map"></a> END_PROPSET_MAP
Las marcas de final de la propiedad establece entradas de mapa.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
END_PROPSET_MAP()  
```  
  
#### <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="property_info_entry"></a> PROPERTY_INFO_ENTRY
Representa una propiedad concreta de un conjunto de propiedades.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROPERTY_INFO_ENTRY(dwPropID)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *dwPropID*  
 [in] Un [DBPROPID](https://msdn.microsoft.com/library/ms723882.aspx) GUID para identificar una propiedad del conjunto de valor que se puede usar junto con la propiedad.  
  
#### <a name="remarks"></a>Comentarios  
 Esta macro establece el valor de propiedad de tipo `DWORD` en un valor predeterminado definido en ATLDB. H. Para establecer la propiedad en un valor de su elección, use [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md). Para establecer el [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) y [DBPROPFLAGS](https://msdn.microsoft.com/library/ms724342.aspx) para la propiedad al mismo tiempo, use [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
#### <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="property_info_entry_ex"></a> PROPERTY_INFO_ENTRY_EX
Representa una propiedad concreta de un conjunto de propiedades.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROPERTY_INFO_ENTRY_EX(dwPropID, vt, dwFlags, value, options)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *dwPropID*  
 [in] Un [DBPROPID](https://msdn.microsoft.com/library/ms723882.aspx) GUID para identificar una propiedad del conjunto de valor que se puede usar junto con la propiedad.  
  
 *vt*  
 [in] El [VARTYPE](http://msdn.microsoft.com/317b911b-1805-402d-a9cb-159546bc88b4) de esta entrada de propiedad.  
  
 *dwFlags*  
 [in] Un [DBPROPFLAGS](https://msdn.microsoft.com/library/ms724342.aspx) valor que describe esta entrada de propiedad.  
  
 *valor*  
 [in] El valor de la propiedad de tipo `DWORD`.  
  
 *Opciones*  
 DBPROPOPTIONS_REQUIRED o DBPROPOPTIONS_SETIFCHEAP. Normalmente, un proveedor no necesita establecer *opciones* puesto que se establece por el consumidor.  
  
#### <a name="remarks"></a>Comentarios  
 Con esta macro, puede especificar directamente el valor de propiedad de tipo `DWORD` así como opciones y marcas. Para establecer simplemente una propiedad a un valor predeterminado definido en ATLDB.H, use [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Para establecer una propiedad a un valor de su elección, sin establecer opciones ni marcas en ella, use [PROPERTY_INFO_ENTRY_VALUE](../../data/oledb/property-info-entry-value.md).  
  
#### <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="property_info_entry_value"></a> PROPERTY_INFO_ENTRY_VALUE
Representa una propiedad concreta de un conjunto de propiedades.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROPERTY_INFO_ENTRY_VALUE(dwPropID, value)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *dwPropID*  
 [in] Un [DBPROPID](https://msdn.microsoft.com/library/ms723882.aspx) GUID para identificar una propiedad del conjunto de valor que se puede usar junto con la propiedad.  
  
 *valor*  
 [in] El valor de la propiedad de tipo `DWORD`.  
  
#### <a name="remarks"></a>Comentarios  
 Con esta macro, puede especificar directamente el valor de propiedad de tipo `DWORD`. Para establecer la propiedad al valor predeterminado definido en ATLDB. H, use [PROPERTY_INFO_ENTRY](../../data/oledb/property-info-entry.md). Para establecer el valor, indicadores y opciones para la propiedad, utilice [PROPERTY_INFO_ENTRY_EX](../../data/oledb/property-info-entry-ex.md).  
  
#### <a name="example"></a>Ejemplo  
 Vea [BEGIN_PROPSET_MAP](../../data/oledb/begin-propset-map.md).  

### <a name="begin_provider_column_map"></a> BEGIN_PROVIDER_COLUMN_MAP
Marca el principio de las entradas de asignación de columna de proveedor.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
BEGIN_PROVIDER_COLUMN_MAP(theClass)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *theClass*  
 [in] El nombre de la clase a la que pertenece esta asignación.  
  
#### <a name="example"></a>Ejemplo  
 Este es un mapa de columnas del proveedor de ejemplo:  
  
 [!code-cpp[NVC_OLEDB_Provider#4](../../data/oledb/codesnippet/cpp/begin-provider-column-map_1.h)]  

### <a name="end_provider_column_map"></a> END_PROVIDER_COLUMN_MAP
Marca el final de las entradas de asignación de columna de proveedor.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
END_PROVIDER_COLUMN_MAP()  
```  
  
#### <a name="example"></a>Ejemplo  
 Consulte [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  

### <a name="provider_column_entry"></a> PROVIDER_COLUMN_ENTRY
Representa una columna específica admitida por el proveedor.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY (name, ordinal, member)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 *Ordinal*  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 *Miembro*  
 [in] La variable de miembro en `dataClass` correspondiente a la columna.  

### <a name="provider_column_entry_fixed"></a> PROVIDER_COLUMN_ENTRY_FIXED
Representa una columna específica admitida por el proveedor.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_FIXED(name, ordinal, dbtype, member)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 *Ordinal*  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 *DbType*  
 [in] El tipo de datos en [DBTYPE](https://msdn.microsoft.com/library/ms711251.aspx).  
  
 *Miembro*  
 [in] La variable de miembro en `dataClass` que almacena los datos.  
  
#### <a name="remarks"></a>Comentarios  
 Permite especificar el tipo de datos de columna.  
  
#### <a name="example"></a>Ejemplo  
 Consulte [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).  

### <a name="provider_column_entry_gn"></a> PROVIDER_COLUMN_ENTRY_GN
Representa una columna específica admitida por el proveedor.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_GN (name, ordinal, flags, colSize, dbtype, precision, scale, guid)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 *Ordinal*  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 *flags*  
 [in] Especifica cómo se devuelven datos. Consulte la `dwFlags` descripción en [estructuras DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx).  
  
 *colSize*  
 [in] El tamaño de columna.  
  
 *DbType*  
 [in] Indica el tipo de datos del valor. Consulte la `wType` descripción en [estructuras DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx).  
  
 *precision*  
 [in] Indica la precisión que se utilizará al obtener los datos si *dbType* es DBTYPE_NUMERIC o DBTYPE_DECIMAL. Consulte la `bPrecision` descripción en [estructuras DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx).  
  
 *Escala*  
 [in] Indica la escala que se utilizará al obtener los datos si dbType es DBTYPE_NUMERIC o DBTYPE_DECIMAL. Consulte la `bScale` descripción en [estructuras DBBINDING](https://msdn.microsoft.com/library/ms716845.aspx).  
  
 *GUID*  
 Un conjunto de filas de esquema GUID. Consulte [IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx) en el *referencia del programador de OLE DB* para obtener una lista de conjuntos de filas de esquema y sus GUID.  
  
#### <a name="remarks"></a>Comentarios  
 Permite especificar el tamaño de la columna, tipo de datos, precisión, escala y GUID del conjunto de filas de esquema.  

### <a name="provider_column_entry_length"></a> PROVIDER_COLUMN_ENTRY_LENGTH
Representa una columna específica admitida por el proveedor.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_LENGTH(name, ordinal, size, member)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 *Ordinal*  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 *size*  
 [in] El tamaño de columna en bytes.  
  
 *Miembro*  
 [in] La variable de miembro en `dataClass` que almacena los datos de columna.  
  
#### <a name="remarks"></a>Comentarios  
 Permite especificar el tamaño de columna.  
  
#### <a name="example"></a>Ejemplo  
 Consulte [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md). 

### <a name="provider_column_entry_str"></a> PROVIDER_COLUMN_ENTRY_STR
Representa una columna específica admitida por el proveedor.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_STR(name, ordinal, member)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 *Ordinal*  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 *Miembro*  
 [in] La variable de miembro de la clase de datos que almacena los datos.  
  
#### <a name="remarks"></a>Comentarios  
 Use esta macro, cuando los datos de columna se supone que [DBTYPE_STR](https://msdn.microsoft.com/library/ms711251.aspx).  
  
#### <a name="example"></a>Ejemplo  
 Consulte [BEGIN_PROVIDER_COLUMN_MAP](../../data/oledb/begin-provider-column-map.md).   

### <a name="provider_column_entry_type_length"></a> PROVIDER_COLUMN_ENTRY_TYPE_LENGTH
Representa una columna específica admitida por el proveedor.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_TYPE_LENGTH(name, ordinal, dbtype, size, member)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 *Ordinal*  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 *DbType*  
 [in] El tipo de datos en [DBTYPE](https://msdn.microsoft.com/library/ms711251.aspx).  
  
 *size*  
 [in] El tamaño de columna en bytes.  
  
 *Miembro*  
 [in] La variable de miembro de la clase de datos que almacena los datos.  
  
#### <a name="remarks"></a>Comentarios  
 Similar a [PROVIDER_COLUMN_ENTRY_LENGTH](../../data/oledb/provider-column-entry-length.md) , pero también permite especificar el tipo de datos de la columna, así como el tamaño.  

### <a name="provider_column_entry_wstr"></a> PROVIDER_COLUMN_ENTRY_WSTR
Representa una columna específica admitida por el proveedor.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
PROVIDER_COLUMN_ENTRY_WSTR(name, ordinal, member)  
```  
  
#### <a name="parameters"></a>Parámetros  
 *name*  
 [in] El nombre de columna.  
  
 *Ordinal*  
 [in] El número de columna. A menos que la columna es una columna de marcador, el número de columna no debe ser 0.  
  
 *Miembro*  
 [in] La variable de miembro de la clase de datos que almacena los datos.  
  
#### <a name="remarks"></a>Comentarios  
 Use esta macro, cuando los datos de columna están un valor null termina la cadena de caracteres Unicode, [DBTYPE_WSTR](https://msdn.microsoft.com/library/ms711251.aspx).  

### <a name="begin_schema_map"></a> BEGIN_SCHEMA_MAP
Indica el principio de una asignación de esquema.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
BEGIN_SCHEMA_MAP(SchemaClass);  
```  
  
#### <a name="parameters"></a>Parámetros  
 *SchemaClass*  
 La clase que contiene el mapa. Normalmente será la clase de sesión.  
  
#### <a name="remarks"></a>Comentarios  
 Consulte [IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx) en el SDK de Windows para obtener más información acerca de los conjuntos de filas de esquema.  

### <a name="end_schema_map"></a> END_SCHEMA_MAP
Denota el final de la asignación de esquema.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
END_SCHEMA_MAP()  
```  
  
#### <a name="see-also"></a>Vea también  
 [IDBSchemaRowsetImpl (Clase)](../../data/oledb/idbschemarowsetimpl-class.md)

### <a name="schema_entry"></a> SCHEMA_ENTRY
Asocia un GUID a una clase.  
  
#### <a name="syntax"></a>Sintaxis  
  
```cpp
SCHEMA_ENTRY(guid,  
   rowsetClass);   
```  
  
#### <a name="parameters"></a>Parámetros  
 *GUID*  
 Un conjunto de filas de esquema GUID. Consulte [IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx) en el *referencia del programador de OLE DB* para obtener una lista de conjuntos de filas de esquema y sus GUID.  
  
 *RowsetClass*  
 La clase que se crearán para representar el conjunto de filas de esquema.  
  
#### <a name="remarks"></a>Comentarios  
 [IDBSchemaRowsetImpl](../../data/oledb/idbschemarowsetimpl-class.md) puede, a continuación, consulta el mapa para obtener una lista de GUID, o puede crear un conjunto de filas si se le asigna un GUID. El conjunto de filas de esquema `IDBSchemaRowsetImpl` crea es similar a un estándar `CRowsetImpl`-clase derivada, salvo que debe proporcionar un `Execute` método que tiene la firma siguiente:  
  
```cpp  
HRESULT Execute (LONG* pcRowsAffected,  
    ULONG cRestrictions,  
    const VARIANT* rgRestrictions);  
```  
  
 Esto `Execute` función rellena los datos del conjunto de filas. Crea el Asistente para proyectos ATL, como se describe en [IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx) en el *referencia del programador de OLE DB*, tres inicial conjuntos de filas de esquema en el proyecto para cada uno de los tres esquemas de OLE DB obligatorios:  
  
-   DBSCHEMA_TABLES  
  
-   DBSCHEMA_COLUMNS  
  
-   DBSCHEMA_PROVIDER_TYPES  
  
 El asistente también agrega tres entradas correspondientes en la asignación de esquema. Consulte [crear un proveedor OLE DB plantilla](../../data/oledb/creating-an-ole-db-provider.md) para obtener más información sobre el uso del Asistente para crear un proveedor.  
  
## <a name="see-also"></a>Vea también  
 [Plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-cpp.md)   
 [Arquitectura de la plantilla de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)   
 [Creación de un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)   
 [Referencia de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-templates-reference.md)    
 [Macros para plantillas de proveedores OLE DB](../../data/oledb/macros-for-ole-db-provider-templates.md)   