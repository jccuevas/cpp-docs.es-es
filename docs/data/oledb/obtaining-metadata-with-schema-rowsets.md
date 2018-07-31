---
title: Obtener metadatos con conjuntos de filas de esquema | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: 9d86984dc67dd5cbea6fe52ff1c8b099e5b061f5
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337195"
---
# <a name="obtaining-metadata-with-schema-rowsets"></a>Obtener metadatos con conjuntos de filas de esquema
En ciertas ocasiones necesitará obtener información sobre un proveedor, un conjunto de filas, una tabla, ciertas columnas u otros datos relacionados con la base de datos sin abrir el conjunto de filas. Los datos sobre la estructura de la base de datos se denominan metadatos y se pueden recuperar con métodos diversos. Uno de ellos consiste en usar conjuntos de filas de esquema.  
  
 Plantillas OLE DB proporcionan un conjunto de clases para recuperar información de esquema; Estas clases crean conjuntos de filas de esquema predefinidos y se enumeran en [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
> [!NOTE]
>  Si usa OLAP y hay conjuntos de filas no compatibles con las clases de conjunto de filas de esquema (por ejemplo, si tiene un número variable de columnas), considere la posibilidad de usar `CManualAccessor` o `CDynamicAccessor`. Puede desplazarse por las columnas y usar instrucciones case para controlar los posibles tipos de datos de cada columna.  
  
## <a name="catalogschema-model"></a>Modelo de esquema y catálogo  
 ANSI SQL define un modelo de esquema y catálogo para almacenes de datos. OLE DB usa este modelo. En él, los catálogos (bases de datos) contienen esquemas, y estos contienen tablas.  
  
-   **Catálogo** un catálogo es otro nombre para una base de datos. Consiste en una colección de esquemas relacionados. Para enumerar los catálogos (bases de datos) pertenecientes a un origen de datos determinado, use [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md). Dado que muchas bases de datos solo tienen un catálogo, a los metadatos a veces se les denomina simplemente información de esquema.  
  
-   **Esquema** un esquema es una colección de objetos de base de datos que se han creado por un usuario determinado o le pertenecen. Para enumerar los esquemas que pertenecen a un usuario determinado, use [CSchemata](../../data/oledb/cschemata-cschematainfo.md).  
  
     En términos de Microsoft SQL Server y ODBC 2.x, un esquema es un propietario (por ejemplo, dbo es un nombre de esquema típico). Además, SQL Server almacena los metadatos en un conjunto de tablas: una tabla contiene una lista de todas las tablas y otra tabla contiene una lista de todas las columnas. No existe equivalente al esquema en las bases de datos de Microsoft Access.  
  
-   **Tabla** las tablas son colecciones de columnas dispuestas en un orden específico. Para enumerar las tablas definidas en un determinado catálogo (base de datos) e información sobre esas tablas, use [CTables](../../data/oledb/ctables-ctableinfo.md)).  
  
## <a name="restrictions"></a>Restricciones  
 Cuando consulte la información de esquema, puede especificar el tipo de información que le interesa a través de las restricciones. Considere las restricciones como un filtro o un calificador de una consulta. Por ejemplo, observe la consulta siguiente:  
  
```sql  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name` es una restricción. Este es un ejemplo muy sencillo, con una sola restricción. Las clases de conjunto de filas de esquema son compatibles con varias restricciones.  
  
 El [clases de definición de tipo de conjunto de filas de esquema](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) encapsular todos los conjuntos de filas de esquema OLE DB, por lo que puede tener acceso a un conjunto de filas de esquema al igual que cualquier otro conjunto de filas mediante la creación de instancias y ábralo. Por ejemplo, la clase typedef [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) se define como:  
  
```cpp  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 El [CRestrictions](../../data/oledb/crestrictions-class.md) clase proporciona la compatibilidad con las restricciones. Después de crear una instancia del conjunto de filas de esquema, llame a [CRestrictions:: Open](../../data/oledb/crestrictions-open.md). Este método devuelve un conjunto de resultados basado en las restricciones especificadas.  
  
 Para especificar restricciones, consulte [Apéndice B: Schema Rowsets](http://go.microsoft.com/fwlink/p/?linkid=64681) y buscar el conjunto de filas que está usando. Por ejemplo, `CColumns` corresponde a la [conjunto de filas COLUMNS](http://go.microsoft.com/fwlink/p/?linkid=64682); ese tema enumeran las columnas de restricción en el conjunto de filas COLUMNS: TABLE_CATALOG, TABLE_SCHEMA, TABLE_NAME, COLUMN_NAME. Debe seguir este orden al especificar las restricciones.  
  
 Por lo tanto, por ejemplo, si desea restringir por nombre de tabla, observe que TABLE_NAME es la tercera columna de restricción y, a continuación, llame a `Open`, especificando el nombre de tabla como el tercer parámetro de restricción, tal como se muestra en el ejemplo siguiente.  
  
#### <a name="to-use-schema-rowsets"></a>Para usar los conjuntos de filas de esquema:  
  
1.  Debe incluir el archivo de encabezado Atldbsch.h (evidentemente, también necesita Atldbcli.h para resultar compatible con los consumidores).  
  
2.  Cree una instancia de un objeto de conjunto de filas de esquema en el archivo de encabezado del documento o del consumidor. Si desea información de la tabla, declare un `CTables` objeto; si desea obtener información de columna, declare un `CColumns` objeto. Este ejemplo muestra cómo recuperar las columnas de la tabla authors:  
  
    ```cpp  
    CDataSource ds;  
    ds.Open();  
    CSession ss;  
    ss.Open();  
    CColumns ColumnSchemaRowset;  
    // TABLE_NAME is the third restriction column, so  
    // specify "authors" as the third restriction parameter:  
    hr = ColumnSchemaRowset.Open(ss, NULL, NULL, "authors");  
    hr = ColumnSchemaRowset.MoveFirst();  
    while (hr == S_OK)  
    {  
       hr = ColumnSchemaRowset.MoveNext();  
    }  
    ```  
  
3.  Para capturar la información, acceda al miembro de datos correspondiente al objeto de conjunto de filas de esquema (por ejemplo, `ColumnSchemaRowset.m_szColumnName`). Esto corresponde a COLUMN_NAME. Para ver qué columna OLE DB corresponde cada miembro de datos, consulte [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md).  
  
 Para la referencia del conjunto de filas de esquema, se proporcionan definiciones de tipos en las plantillas OLE DB (consulte [clases de conjunto de filas de esquema y clases Typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)).  
  
 Para obtener más información sobre los conjuntos de filas de esquema OLE DB, incluidas las columnas de restricción, consulte [Apéndice B: Schema Rowsets](http://go.microsoft.com/fwlink/p/?linkid=64681) en referencia de la base de datos del programador de OLE.  
  
 Para obtener ejemplos más complejos de cómo usar las clases de conjunto de filas de esquema, vea el [CatDB](http://msdn.microsoft.com/003d516b-2bf6-444e-8be5-4ebaa0b66046) y [DBViewer](http://msdn.microsoft.com/07620f99-c347-4d09-9ebc-2459e8049832) ejemplos.  
  
 Para obtener información sobre la compatibilidad con el proveedor de conjuntos de filas de esquema, vea [admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md).  
  
## <a name="see-also"></a>Vea también  
 [Usar descriptores de acceso](../../data/oledb/using-accessors.md)