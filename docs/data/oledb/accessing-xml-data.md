---
title: "Obtener acceso a datos XML | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStreamRowset (clase), recuperar datos XML"
  - "CXMLAccessor (clase), recuperar datos XML"
  - "datos [C++], acceso a datos XML"
  - "acceso a datos [C++], datos XML"
  - "conjuntos de filas [C++], recuperar datos XML"
  - "XML [C++], obtener acceso a datos"
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
caps.latest.revision: 13
caps.handback.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Obtener acceso a datos XML
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Existen dos métodos independientes para recuperar datos XML de un origen de datos: mediante [CStreamRowset](../../data/oledb/cstreamrowset-class.md) o [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).  
  
|Funcionalidad|CStreamRowset|CXMLAccessor|  
|-------------------|-------------------|------------------|  
|Volumen de datos transferido|Recupera datos de todas las columnas y filas a la vez.|Recupera datos de todas las columnas, pero sólo una fila a la vez.  Para navegar por las filas se requieren métodos como `MoveNext`.|  
|Dar formato a la cadena|SQL Server da formato a la cadena XML y la envía al consumidor.|Recupera datos del conjunto de filas en su formato nativo \(solicitudes que el proveedor envía como cadenas Unicode\) y a continuación compila la cadena que contiene los datos en formato XML.|  
|Control sobre el formato|Existe cierto control sobre el formato de la cadena XML al establecer algunas propiedades específicas de SQL Server 2000.|No se dispone de control sobre el formato de la cadena XML generada.|  
  
 Aunque `CStreamRowset` proporciona una eficacia más amplia para recuperar datos en formato XML, sólo se utiliza en SQL Server 2000.  
  
## Recuperar datos XML mediante CStreamRowset  
 Se especifica [CStreamRowset](../../data/oledb/cstreamrowset-class.md) como tipo de conjunto de filas en la declaración de `CCommand` o `CTable`.  Se puede utilizar con nuestro descriptor de acceso personal o sin descriptor de acceso, como por ejemplo:  
  
```  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
 O bien  
  
```  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
 Normalmente, cuando se llama a `CCommand::Open` \(especificando, por ejemplo, `CRowset` como la clase `TRowset`\), se obtiene un puntero `IRowset`.  `ICommand::Execute` devuelve un puntero `IRowset`, que se almacena en el miembro `m_spRowset` del objeto `CRowset`.  Los métodos como `MoveFirst`, `MoveNext` y `GetData` usan ese puntero para recuperar los datos.  
  
 Por el contrario, cuando se llama a `CCommand::Open` \(pero se especifica `CStreamRowset` como la clase `TRowset`\), `ICommand::Execute` devuelve un puntero `ISequentialStream`, que se almacena en el miembro de datos `m_spStream` de [CStreamRowset](../../data/oledb/cstreamrowset-class.md).  Después, se puede usar el método `Read` para recuperar los datos \(cadena Unicode\) en formato XML.  Por ejemplo:  
  
```  
myCmd.m_spStream->Read()  
```  
  
 SQL Server 2000 aplica el formato XML y devuelve todas las columnas y filas del conjunto de filas como una sola cadena XML.  
  
 Para obtener un ejemplo en el que se utiliza el método `Read`, vea "Agregar compatibilidad con XML al consumidor" en [Implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md).  
  
> [!NOTE]
>  La compatibilidad con XML mediante `CStreamRowset` sólo funciona con SQL Server 2000 y requiere el uso del proveedor OLE DB para SQL Server 2000 \(instalado con MDAC\).  
  
## Recuperar datos XML mediante CXMLAccessor  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) permite obtener acceso a los datos de un origen de datos como datos de cadena cuando no se conoce el esquema del almacén de datos.  `CXMLAccessor` funciona de manera similar que `CDynamicStringAccessorW`, salvo que el primero convierte todos los datos a los que se obtiene acceso desde el almacén de datos como datos con formato \(etiquetas\) XML.  Los nombres de etiqueta XML coinciden con los nombres de columna del almacén de datos en la medida de lo posible.  
  
 `CXMLAccessor` se utiliza como las demás clases de descriptor de acceso, pasándola como un parámetro de plantilla a `CCommand` o `CTable`:  
  
```  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
 Utilice [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) para recuperar datos de la tabla, una fila cada vez, y métodos como `MoveNext` para navegar por las filas, por ejemplo:  
  
```  
// Open data source, session, and rowset  
hr = rs.MoveFirst();  
while( SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )  
{  
    CStringW strRowData;  
    myCmd.GetXMLRowData(strRowData);  
  
    printf_s( "%S\n", strRowData );  
  
    hr = rs.MoveNext();  
}  
```  
  
 [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) se puede usar para recuperar la información de columnas \(tipos de datos\) como datos de cadena con formato XML.  
  
## Vea también  
 [Utilizar descriptores de acceso](../../data/oledb/using-accessors.md)