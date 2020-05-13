---
title: Obtener metadatos con conjuntos de filas de esquema
ms.date: 10/24/2018
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
ms.openlocfilehash: e04b9a335c60cefdc28be2347ef1f0762c424d8e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210137"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Obtener metadatos con conjuntos de filas de esquema

En ciertas ocasiones necesitará obtener información sobre un proveedor, un conjunto de filas, una tabla, ciertas columnas u otros datos relacionados con la base de datos sin abrir el conjunto de filas. Los datos sobre la estructura de la base de datos se denominan metadatos y se pueden recuperar con métodos diversos. Uno de ellos consiste en usar conjuntos de filas de esquema.

OLE DB plantillas proporcionan un conjunto de clases para recuperar información de esquema; Estas clases crean conjuntos de filas de esquema predefinidos y se enumeran en [clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

> [!NOTE]
> Si usa OLAP y hay conjuntos de filas no compatibles con las clases de conjunto de filas de esquema (por ejemplo, si tiene un número variable de columnas), considere la posibilidad de usar `CManualAccessor` o `CDynamicAccessor`. Puede desplazarse por las columnas y usar instrucciones case para controlar los posibles tipos de datos de cada columna.

## <a name="catalogschema-model"></a>Modelo de esquema y catálogo

ANSI SQL define un modelo de esquema y catálogo para almacenes de datos. OLE DB usa este modelo. En este modelo, los catálogos (bases de datos) tienen tablas y esquemas.

- **Catálogo** de Un catálogo es otro nombre para una base de datos. Es una colección de esquemas relacionados. Para enumerar los catálogos (bases de datos) que pertenecen a un origen de datos determinado, use [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Dado que muchas bases de datos tienen un solo catálogo, a veces los metadatos se denominan información de esquema.

- **Esquema** de Un esquema es una colección de objetos de base de datos que son propiedad de un usuario determinado o que se han creado. Para enumerar los esquemas que pertenecen a un usuario determinado, use [CSchemata](../../data/oledb/cschemata-cschematainfo.md).

   En los términos de Microsoft SQL Server y ODBC 2. x, un esquema es un propietario (por ejemplo, DBO es un nombre de esquema típico). Además, SQL Server almacena metadatos en un conjunto de tablas: una tabla contiene una lista de todas las tablas y otra tabla contiene una lista de todas las columnas. No hay ningún equivalente a un esquema en una base de datos de Microsoft Access.

- **Tabla** de Las tablas son colecciones de columnas organizadas en pedidos concretos. Para enumerar las tablas definidas en un catálogo (base de datos) determinado e información sobre esas tablas, use [CTables](../../data/oledb/ctables-ctableinfo.md)).

## <a name="restrictions"></a>Restricciones

Al consultar información de esquema, puede usar restricciones para especificar el tipo de información en el que está interesado. Considere las restricciones como un filtro o un calificador de una consulta. Por ejemplo, observe la consulta siguiente:

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` es una restricción. Este es un ejemplo sencillo con una sola restricción; las clases de conjunto de filas de esquema admiten varias restricciones.

Las [clases typedef de conjunto de filas de esquema](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) encapsulan todos los conjuntos de filas de esquema OLE DB para que pueda tener acceso a un conjunto de filas de esquema como cualquier otro conjunto de filas; para ello, cree una instancia y ábralo. Por ejemplo, la clase typedef [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) se define como:

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

La clase [CRestrictions](../../data/oledb/crestrictions-class.md) proporciona la compatibilidad con restricciones. Después de crear una instancia del conjunto de filas de esquema, llame a [CRestrictions:: Open](../../data/oledb/crestrictions-open.md). Este método devuelve un conjunto de resultados basado en las restricciones especificadas.

Para especificar las restricciones, vea el [Apéndice B: conjuntos de filas de esquema](/previous-versions/windows/desktop/ms712921(v=vs.85)) y buscar el conjunto de filas que está usando. Por ejemplo, `CColumns` corresponde al [conjunto de filas Columns](/previous-versions/windows/desktop/ms723052(v=vs.85)); en ese tema se enumeran las columnas de restricción del conjunto de filas COLUMNs: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME COLUMN_NAME. Debe seguir este orden al especificar las restricciones.

Por lo tanto, por ejemplo, si desea restringir por nombre de tabla, TABLE_NAME es la tercera columna de restricción y, a continuación, llamar a `Open`, especificando el nombre de tabla deseado como el tercer parámetro de restricción, tal como se muestra en el ejemplo siguiente.

### <a name="to-use-schema-rowsets"></a>Para usar los conjuntos de filas de esquema:

1. Incluya el archivo de encabezado `Atldbsch.h` (también necesita `Atldbcli.h` para la compatibilidad con consumidores).

1. Cree una instancia de un objeto de conjunto de filas de esquema en el archivo de encabezado del documento o del consumidor. Si desea información de tabla, declare un objeto `CTables`; Si desea información de columna, declare un objeto `CColumns`. Este ejemplo muestra cómo recuperar las columnas de la tabla authors:

    ```cpp
    CDataSource ds;
    ds.Open();
    CSession ss;
    ss.Open(ds);
    CColumns columnSchemaRowset;
    // TABLE_NAME is the third restriction column, so
    // specify "authors" as the third restriction parameter:
    HRESULT hr = columnSchemaRowset.Open(ss, NULL, NULL, L"authors");
    hr = columnSchemaRowset.MoveFirst();
    while (hr == S_OK)
    {
       hr = columnSchemaRowset.MoveNext();
    }
    ```

1. Para capturar la información, acceda al miembro de datos correspondiente al objeto de conjunto de filas de esquema (por ejemplo, `ColumnSchemaRowset.m_szColumnName`). Este miembro de datos corresponde a COLUMN_NAME. Para ver a qué OLE DB columna corresponde cada miembro de datos, consulte [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).

Para consultar la referencia del conjunto de filas de esquema, las clases typedef proporcionadas en las plantillas de OLE DB (vea clases [de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).

Para obtener más información sobre OLE DB conjuntos de filas de esquema, incluidas las columnas de restricción, vea [Apéndice B: conjuntos de filas de esquema](/previous-versions/windows/desktop/ms712921(v=vs.85)) en la **Referencia del programador de OLE DB**.

Para obtener ejemplos más complejos de cómo usar las clases de conjunto de filas de esquema, vea los ejemplos [CatDB](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) y [DBViewer](https://github.com/Microsoft/VCSamples/tree/master/VC2010Samples/ATL/OLEDB/Consumer) .

Para obtener información sobre la compatibilidad del proveedor con los conjuntos de filas de esquema, vea [admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md).

## <a name="see-also"></a>Consulte también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)
