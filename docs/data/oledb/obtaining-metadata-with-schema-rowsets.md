---
title: Obtener metadatos con conjuntos de filas de esquema | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- schema rowsets, getting OLE DB provider metadata
- OLE DB consumer templates, getting provider metadata
- metadata, getting (OLE DB Templates)
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a3bedc2057ed90376912838953bcd0a7a3a7106f
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50072881"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Obtener metadatos con conjuntos de filas de esquema

En ciertas ocasiones necesitará obtener información sobre un proveedor, un conjunto de filas, una tabla, ciertas columnas u otros datos relacionados con la base de datos sin abrir el conjunto de filas. Los datos sobre la estructura de la base de datos se denominan metadatos y se pueden recuperar con métodos diversos. Uno de ellos consiste en usar conjuntos de filas de esquema.

Plantillas OLE DB proporcionan un conjunto de clases para recuperar información de esquema; Estas clases crean conjuntos de filas de esquema predefinidos y se enumeran en [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).

> [!NOTE]
> Si usa OLAP y hay conjuntos de filas no compatibles con las clases de conjunto de filas de esquema (por ejemplo, si tiene un número variable de columnas), considere la posibilidad de usar `CManualAccessor` o `CDynamicAccessor`. Puede desplazarse por las columnas y usar instrucciones case para controlar los posibles tipos de datos de cada columna.

## <a name="catalogschema-model"></a>Modelo de esquema y catálogo

ANSI SQL define un modelo de esquema y catálogo para almacenes de datos. OLE DB usa este modelo. En este modelo, los catálogos (bases de datos) tienen esquemas y los esquemas tienen tablas.

- **Catálogo** un catálogo es otro nombre para una base de datos. Es una colección de esquemas relacionados. Para enumerar los catálogos (bases de datos) pertenecientes a un origen de datos determinado, use [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Dado que muchas bases de datos tienen solo un catálogo, los metadatos a veces se denominan información de esquema.

- **Esquema** un esquema es una colección de objetos de base de datos que se han creado por un usuario determinado o le pertenecen. Para enumerar los esquemas que pertenecen a un usuario determinado, use [CSchemata](../../data/oledb/cschemata-cschematainfo.md).

   En términos de Microsoft SQL Server y ODBC 2.x, un esquema es un propietario (por ejemplo, dbo es un nombre de esquema típico). Además, SQL Server almacena los metadatos en un conjunto de tablas: una tabla contiene una lista de todas las tablas y otra tabla contiene una lista de todas las columnas. No hay ningún equivalente a un esquema en una base de datos de Microsoft Access.

- **Tabla** las tablas son colecciones de columnas dispuestas en un orden específico. Para enumerar las tablas definidas en un determinado catálogo (base de datos) e información sobre esas tablas, use [CTables](../../data/oledb/ctables-ctableinfo.md)).

## <a name="restrictions"></a>Restricciones

Al consultar información de esquema, puede usar las restricciones para especificar el tipo de información que interesa. Considere las restricciones como un filtro o un calificador de una consulta. Por ejemplo, observe la consulta siguiente:

```sql
SELECT * FROM authors WHERE l_name = 'pivo'
```

`l_name` es una restricción. Este es un ejemplo simple con solo una restricción; las clases de conjunto de filas de esquema admiten varias restricciones.

El [clases de definición de tipo de conjunto de filas de esquema](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) encapsular todos los conjuntos de filas de esquema OLE DB, por lo que puede tener acceso a un conjunto de filas de esquema al igual que cualquier otro conjunto de filas mediante la creación de instancias y ábralo. Por ejemplo, la clase typedef [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) se define como:

```cpp
CRestrictions<CAccessor<CColumnsInfo>
```

El [CRestrictions](../../data/oledb/crestrictions-class.md) clase proporciona la compatibilidad con las restricciones. Después de crear una instancia del conjunto de filas de esquema, llame a [CRestrictions:: Open](../../data/oledb/crestrictions-open.md). Este método devuelve un conjunto de resultados basado en las restricciones especificadas.

Para especificar restricciones, consulte [Apéndice B: Schema Rowsets](/previous-versions/windows/desktop/ms712921) y buscar el conjunto de filas que esté usando. Por ejemplo, `CColumns` corresponde a la [conjunto de filas COLUMNS](/previous-versions/windows/desktop/ms723052\(v%3dvs.85\)); ese tema enumeran las columnas de restricción en el conjunto de filas COLUMNS: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME. Debe seguir este orden al especificar las restricciones.

Por lo tanto, por ejemplo, si desea restringir por nombre de tabla, TABLE_NAME es la tercera columna de restricción y, a continuación, llame `Open`, especificando el nombre de tabla deseado como tercer parámetro de restricción, tal como se muestra en el ejemplo siguiente.

### <a name="to-use-schema-rowsets"></a>Para usar los conjuntos de filas de esquema:

1. Incluir el archivo de encabezado `Atldbsch.h` (necesita `Atldbcli.h` para admitir consumidores).

1. Cree una instancia de un objeto de conjunto de filas de esquema en el archivo de encabezado del documento o del consumidor. Si desea información de la tabla, declare un `CTables` objeto; si desea obtener información de columna, declare un `CColumns` objeto. Este ejemplo muestra cómo recuperar las columnas de la tabla authors:

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

1. Para capturar la información, acceda al miembro de datos correspondiente al objeto de conjunto de filas de esquema (por ejemplo, `ColumnSchemaRowset.m_szColumnName`). Este miembro de datos corresponde a COLUMN_NAME. Para ver qué columna OLE DB corresponde cada miembro de datos, consulte [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).

Para la referencia del conjunto de filas de esquema, se proporcionan definiciones de tipos en las plantillas OLE DB (consulte [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).

Para obtener más información sobre los conjuntos de filas de esquema OLE DB, incluidas las columnas de restricción, consulte [Apéndice B: Schema Rowsets](/previous-versions/windows/desktop/ms712921) en el **referencia del programador de OLE DB**.

Para obtener ejemplos más complejos de cómo usar las clases de conjunto de filas de esquema, vea el [CatDB](https://github.com/Microsoft/VCSamples) y [DBViewer](https://github.com/Microsoft/VCSamples) ejemplos.

Para obtener información sobre la compatibilidad con el proveedor de conjuntos de filas de esquema, vea [admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md).

## <a name="see-also"></a>Vea también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)