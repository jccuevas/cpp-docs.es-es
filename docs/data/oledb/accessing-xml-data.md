---
title: Acceso a datos XML | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 654fab0aa5a5bf96e145f37ae4855f556f79bebf
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="accessing-xml-data"></a>Obtener acceso a datos XML
Hay dos métodos independientes para recuperar datos XML de un origen de datos: uno usa [CStreamRowset](../../data/oledb/cstreamrowset-class.md) y los demás usos [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).  
  
|Funcionalidad|CStreamRowset|CXMLAccessor|  
|-------------------|-------------------|------------------|  
|Cantidad de datos transferidos|Recupera datos de todas las columnas y filas a la vez.|Recupera datos de todas las columnas, pero solo una fila cada vez. Desplazarse por las filas con métodos como `MoveNext`.|  
|La cadena de formato|SQL Server da formato a la cadena XML y lo envía al consumidor.|Recupera los datos del conjunto de filas en su formato nativo (solicitudes que el proveedor envía como cadenas Unicode) y, a continuación, crea la cadena que contiene los datos en formato XML.|  
|Control sobre el formato|Tener cierto nivel de control sobre cómo se da formato a la cadena XML al establecer algunas propiedades específicas de SQL Server 2000.|No tiene ningún control sobre el formato de la cadena XML generada.|  
  
 Mientras `CStreamRowset` proporciona una manera más eficaz general de recuperación de datos en formato XML, solo es compatible con SQL Server 2000.  
  
## <a name="retrieving-xml-data-using-cstreamrowset"></a>Recuperar datos XML mediante CStreamRowset  
 Especifique [CStreamRowset](../../data/oledb/cstreamrowset-class.md) como el tipo de conjunto de filas en la `CCommand` o `CTable` declaración. También puede utilizarlo con su propio descriptor de acceso o ningún descriptor de acceso, por ejemplo:  
  
```  
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;  
```  
  
 O bien  
  
```  
CCommand<CNoAccessor, CStreamRowset> myCmd;  
```  
  
 Normalmente cuando se llama a `CCommand::Open` (especificando, por ejemplo, `CRowset` como el `TRowset` clase), obtiene un `IRowset` puntero. `ICommand::Execute`Devuelve un `IRowset` puntero, que se almacena en la `m_spRowset` miembro de la `CRowset` objeto. Métodos como `MoveFirst`, `MoveNext`, y `GetData` usan ese puntero para recuperar los datos.  
  
 Por el contrario, cuando se llama a `CCommand::Open` (pero especifique `CStreamRowset` como el `TRowset` clase), `ICommand::Execute` devuelve un `ISequentialStream` puntero, que se almacena en la `m_spStream` miembro de datos de [CStreamRowset](../../data/oledb/cstreamrowset-class.md). A continuación, utilice el `Read` método para recuperar los datos (cadena Unicode) en formato XML. Por ejemplo:  
  
```  
myCmd.m_spStream->Read()  
```  
  
 SQL Server 2000 aplica el formato XML y devuelve todas las columnas y todas las filas del conjunto de filas como una sola cadena XML.  
  
 Para obtener un ejemplo de uso del `Read` método, vea "Agregar compatibilidad con XML al consumidor" en [implementar un consumidor sencillo](../../data/oledb/implementing-a-simple-consumer.md).  
  
> [!NOTE]
>  Compatibilidad con XML utilizando `CStreamRowset` sólo funciona con SQL Server 2000 y requiere que tenga el proveedor OLE DB para SQL Server 2000 (instalado con MDAC).  
  
## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Recuperar datos XML mediante CXMLAccessor  
 [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) permite obtener acceso a datos desde un origen de datos como datos de cadena cuando no tiene ningún conocimiento del esquema del almacén de datos. `CXMLAccessor`funciona como `CDynamicStringAccessorW` excepto en que el primero convierte todos los datos que se tiene acceso desde el almacén de datos como datos (etiquetados) en formato XML. Los nombres de etiqueta XML coinciden con los nombres de columna del almacén de datos lo más fielmente posible.  
  
 Use `CXMLAccessor` como lo haría con cualquier otra clase de descriptor de acceso, puede pasarlo como un parámetro de plantilla a `CCommand` o `CTable`:  
  
```  
CTable<CXMLAccessor, CRowset> rs;  
```  
  
 Use [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) para recuperar datos de la tabla una fila a la vez y desplazarse por las filas con métodos como `MoveNext`, por ejemplo:  
  
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
  
 Puede usar [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) para recuperar la información de columna (tipo de datos) como datos de cadena con formato XML.  
  
## <a name="see-also"></a>Vea también  
 [Usar descriptores de acceso](../../data/oledb/using-accessors.md)