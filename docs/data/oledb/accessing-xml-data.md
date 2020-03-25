---
title: Obtener acceso a datos XML
ms.date: 10/18/2018
helpviewer_keywords:
- data access [C++], XML data
- XML [C++], accessing data
- CXMLAccessor class, retrieving XML data
- data [C++], XML data access
- rowsets [C++], retrieving XML data
- CStreamRowset class, retrieving XML data
ms.assetid: 6b693d55-a554-4846-8118-e8773b79b572
ms.openlocfilehash: be4225003211449a98d3fbe5fd686b9b8058a651
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80212282"
---
# <a name="accessing-xml-data"></a>Obtener acceso a datos XML

Hay dos métodos independientes para recuperar datos XML de un origen de datos: uno usa [CStreamRowset](../../data/oledb/cstreamrowset-class.md) y el otro usa [CXMLAccessor](../../data/oledb/cxmlaccessor-class.md).

|Funcionalidad|CStreamRowset|CXMLAccessor|
|-------------------|-------------------|------------------|
|Cantidad de datos transferidos|Recupera los datos de todas las columnas y filas a la vez.|Recupera los datos de todas las columnas, pero solo una fila cada vez. Debe navegar por las filas mediante métodos como `MoveNext`.|
|Aplicar formato a la cadena|SQL Server da formato a la cadena XML y la envía al consumidor.|Recupera los datos del conjunto de filas en su formato nativo (solicita que el proveedor lo envíe como cadenas Unicode) y, a continuación, crea la cadena que contiene los datos en formato XML.|
|Control sobre el formato|Tiene cierto nivel de control sobre cómo se da formato a la cadena XML estableciendo algunas SQL Server propiedades específicas de 2000.|No tiene ningún control sobre el formato de la cadena XML generada.|

Aunque `CStreamRowset` proporciona una manera más eficaz de recuperar datos en formato XML, solo es compatible con SQL Server 2000.

## <a name="retrieving-xml-data-using-cstreamrowset"></a>Recuperar datos XML mediante CStreamRowset

Especifique [CStreamRowset](../../data/oledb/cstreamrowset-class.md) como el tipo de conjunto de filas en la declaración de `CCommand` o `CTable`. Puede usarlo con su propio descriptor de acceso o sin descriptor de acceso, por ejemplo:

```cpp
CCommand<CAccessor<CMyAccessor>, CStreamRowset> myCmd;
```

O bien

```cpp
CCommand<CNoAccessor, CStreamRowset> myCmd;
```

Normalmente, cuando se llama a `CCommand::Open` (al especificar, por ejemplo, `CRowset` como la clase `TRowset`), se obtiene un puntero `IRowset`. `ICommand::Execute` devuelve un puntero `IRowset`, que se almacena en el miembro `m_spRowset` del objeto `CRowset`. Los métodos como `MoveFirst`, `MoveNext`y `GetData` usan ese puntero para recuperar los datos.

Por el contrario, cuando se llama a `CCommand::Open` (pero se especifica `CStreamRowset` como la clase `TRowset`), `ICommand::Execute` devuelve un puntero `ISequentialStream`, que se almacena en el miembro de datos `m_spStream` de [CStreamRowset](../../data/oledb/cstreamrowset-class.md). A continuación, use el método `Read` para recuperar los datos de (cadena Unicode) en formato XML. Por ejemplo:

```cpp
myCmd.m_spStream->Read()
```

SQL Server 2000 realiza el formato XML y devuelve todas las columnas y todas las filas del conjunto de filas como una cadena XML.

Para obtener un ejemplo en el que se usa el método `Read`, vea **Agregar compatibilidad con XML al consumidor en la** [implementación de un consumidor simple](../../data/oledb/implementing-a-simple-consumer.md).

> [!NOTE]
> La compatibilidad con XML mediante el uso de `CStreamRowset` solo funciona con SQL Server 2000 y requiere que tenga el proveedor de OLE DB para SQL Server 2000 (instalado con MDAC).

## <a name="retrieving-xml-data-using-cxmlaccessor"></a>Recuperar datos XML mediante CXMLAccessor

[CXMLAccessor](../../data/oledb/cxmlaccessor-class.md) permite tener acceso a los datos de un origen de datos como datos de cadena cuando no se tiene conocimiento del esquema del almacén de datos. `CXMLAccessor` funciona como `CDynamicStringAccessorW`, salvo que el primero convierte todos los datos a los que se tiene acceso desde el almacén de datos como datos con formato XML. Los nombres de las etiquetas XML coinciden con los nombres de columna del almacén de datos lo más cerca posible.

Use `CXMLAccessor` como haría con cualquier otra clase de descriptor de acceso, pasándola como un parámetro de plantilla a `CCommand` o `CTable`:

```cpp
CTable<CXMLAccessor, CRowset> rs;
```

Use [GetXMLRowData](../../data/oledb/cxmlaccessor-getxmlrowdata.md) para recuperar datos de la tabla de una fila cada vez y navegue por las filas mediante métodos como `MoveNext`, por ejemplo:

```cpp
// Open data source, session, and rowset
hr = rs.MoveFirst();

while(SUCCEEDED(hr) && hr != DB_S_ENDOFROWSET )
{
    CStringW strRowData;
    myCmd.GetXMLRowData(strRowData);

    printf_s( "%S\n", strRowData );

    hr = rs.MoveNext();
}
```

Puede usar [GetXMLColumnData](../../data/oledb/cxmlaccessor-getxmlcolumndata.md) para recuperar la información de la columna (tipo de datos) como datos de cadena con formato XML.

## <a name="see-also"></a>Consulte también

[Usar descriptores de acceso](../../data/oledb/using-accessors.md)
