---
title: "Obtener metadatos con conjuntos de filas de esquema | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "metadatos, obtener (plantillas OLE DB)"
  - "plantillas de consumidor OLE DB, obtener metadatos del proveedor"
  - "conjuntos de filas de esquema, obtener metadatos del proveedor OLE DB"
ms.assetid: 6b448461-82fb-4acf-816b-3cbb0ca1d186
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Obtener metadatos con conjuntos de filas de esquema
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

En ciertas ocasiones necesitará obtener información sobre un proveedor, un conjunto de filas, una tabla, ciertas columnas u otros datos relacionados con la base de datos sin abrir el conjunto de filas.  Los datos sobre la estructura de la base de datos se denominan metadatos y se pueden recuperar con métodos diversos.  Uno de ellos consiste en usar conjuntos de filas de esquema.  
  
 Las plantillas OLE DB proporcionan un conjunto de clases para recuperar información de esquema, que crean conjuntos de filas de esquema predefinidos. Se enumeran en [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md).  
  
> [!NOTE]
>  Si usa OLAP y hay conjuntos de filas no compatibles con las clases de conjunto de filas de esquema \(por ejemplo, si tiene un número variable de columnas\), considere la posibilidad de usar `CManualAccessor` o `CDynamicAccessor`.  Puede desplazarse por las columnas y usar instrucciones case para controlar los posibles tipos de datos de cada columna.  
  
## Modelo de esquema y catálogo  
 ANSI SQL define un modelo de esquema y catálogo para almacenes de datos. OLE DB usa este modelo.  En él, los catálogos \(bases de datos\) contienen esquemas, y estos contienen tablas.  
  
-   **Catálogo** Es otro término para designar a una base de datos.  Consiste en una colección de esquemas relacionados.  Puede mostrar los catálogos \(bases de datos\) pertenecientes a un origen de datos determinado con [CCatalog](../../data/oledb/ccatalogs-ccataloginfo.md).  Dado que muchas bases de datos solo tienen un catálogo, a los metadatos a veces se les denomina simplemente información de esquema.  
  
-   **Esquema** Una colección de objetos de base de datos que ha creado un usuario determinado o le pertenecen.  Puede mostrar los esquemas que pertenecen a un usuario determinado con [CSchemata](../../data/oledb/cschemata-cschematainfo.md).  
  
     En terminología de Microsoft SQL Server y ODBC 2.x, un esquema es un propietario \(por ejemplo, dbo es un nombre de esquema típico\).  Además, SQL Server almacena los metadatos en un conjunto de tablas: una contiene una lista con todas las tablas y, otra, una lista con todas las columnas.  No existe equivalente al esquema en las bases de datos de Microsoft Access.  
  
-   **Tabla** Las tablas son colecciones de columnas dispuestas en un orden específico.  Puede obtener una lista de las tablas definidas en un catálogo \(base de datos\) determinado e información sobre estas con [CTables](../../data/oledb/ctables-ctableinfo.md).  
  
## Restricciones  
 Cuando consulte la información de esquema, puede especificar el tipo de información que le interesa a través de las restricciones.  Considere las restricciones como un filtro o un calificador de una consulta.  Por ejemplo, observe la consulta siguiente:  
  
```  
SELECT * FROM authors where l_name = 'pivo'  
```  
  
 `l_name` es una restricción.  Este es un ejemplo muy sencillo, con una sola restricción. Las clases de conjunto de filas de esquema son compatibles con varias restricciones.  
  
 Las [clases de definiciones de tipo de conjunto de filas de esquema](../../data/oledb/schema-rowset-classes-and-typedef-classes.md) encapsulan todos los conjuntos de filas de esquema OLE DB. Para acceder a un conjunto de filas de esquema, al igual que lo haría con cualquier otro conjunto de filas, cree la instancia correspondiente y ábralo.  Por ejemplo, la clase de definiciones de tipo [CColumns](../../data/oledb/ccolumns-ccolumnsinfo.md) se determina de la siguiente forma:  
  
```  
CRestrictions<CAccessor<CColumnsInfo>  
```  
  
 La clase [CRestrictions](../../data/oledb/crestrictions-class.md) ofrece la compatibilidad con las restricciones.  Después de crear una instancia del conjunto de filas de esquema, llame a [CRestrictions::Open](../../data/oledb/crestrictions-open.md).  Este método devuelve un conjunto de resultados basado en las restricciones especificadas.  
  
 Para especificar restricciones, consulte el [apéndice B sobre los conjuntos de filas de esquema](http://go.microsoft.com/fwlink/?LinkId=64681) y busque el conjunto de filas que está usando.  Por ejemplo, **CColumns** se corresponde con este tema sobre el [conjunto de filas COLUMNS](http://go.microsoft.com/fwlink/?LinkId=64682), que enumera las columnas de restricción del conjunto de filas COLUMNS: TABLE\_CATALOG, TABLE\_SCHEMA, TABLE\_NAME, COLUMN\_NAME.  Debe seguir este orden al especificar las restricciones.  
  
 Por ejemplo, si desea restringir por nombre de tabla, observe que TABLE\_NAME es la tercera columna de restricción. A continuación, llame a **Open** y especifique el nombre de tabla que desea como tercer parámetro de restricción, tal como se muestra en el ejemplo siguiente.  
  
#### Para usar los conjuntos de filas de esquema:  
  
1.  Debe incluir el archivo de encabezado Atldbsch.h \(evidentemente, también necesita Atldbcli.h para resultar compatible con los consumidores\).  
  
2.  Cree una instancia de un objeto de conjunto de filas de esquema en el archivo de encabezado del documento o del consumidor.  Si está interesado en la información de tabla, declare un objeto **CTables**. Si prefiere la información de columna, declare un objeto **CColumns** en su lugar.  Este ejemplo muestra cómo recuperar las columnas de la tabla authors:  
  
    ```  
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
  
3.  Para capturar la información, acceda al miembro de datos correspondiente al objeto de conjunto de filas de esquema \(por ejemplo, `ColumnSchemaRowset.m_szColumnName`\).  Esto corresponde a COLUMN\_NAME.  Para ver qué columna OLE DB corresponde a cada miembro de datos, consulte [CColumns, CColumnsInfo](../../data/oledb/ccolumns-ccolumnsinfo.md).  
  
 Para obtener la referencia del conjunto de filas de esquema, se proporcionan clases de definiciones de tipo en las plantillas OLE DB \(consulte [Clases de conjunto de filas de esquema y clases typedef](../../data/oledb/schema-rowset-classes-and-typedef-classes.md)\).  
  
 Para obtener más información sobre los conjuntos de filas de esquema OLE DB, incluidas las columnas de restricción, consulte el [apéndice B sobre los conjuntos de filas de esquema](http://go.microsoft.com/fwlink/?LinkId=64681) en la referencia del programador de OLE DB.  
  
 Para obtener ejemplos más complejos de cómo usar las clases de conjunto de filas de esquema, consulte los ejemplos de [CatDB](http://msdn.microsoft.com/es-es/003d516b-2bf6-444e-8be5-4ebaa0b66046) y [DBViewer](http://msdn.microsoft.com/es-es/07620f99-c347-4d09-9ebc-2459e8049832).  
  
 Para obtener más información sobre la compatibilidad del proveedor con los conjuntos de filas de esquema, consulte [Admitir conjuntos de filas de esquema](../../data/oledb/supporting-schema-rowsets.md).  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)