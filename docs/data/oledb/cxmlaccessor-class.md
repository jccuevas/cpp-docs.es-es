---
title: CXMLAccessor (Clase)
ms.date: 11/04/2016
f1_keywords:
- ATL::CXMLAccessor
- CXMLAccessor
- ATL.CXMLAccessor
- ATL.CXMLAccessor.GetXMLColumnData
- CXMLAccessor::GetXMLColumnData
- CXMLAccessor.GetXMLColumnData
- ATL::CXMLAccessor::GetXMLColumnData
- GetXMLColumnData
- ATL::CXMLAccessor::GetXMLRowData
- ATL.CXMLAccessor.GetXMLRowData
- CXMLAccessor::GetXMLRowData
- CXMLAccessor.GetXMLRowData
- GetXMLRowData
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
ms.openlocfilehash: f25fb3635f70ee9a0e38ddcdbcf373fe6b1b84c8
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211047"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor (Clase)

Permite tener acceso a los orígenes de datos como datos de cadena cuando no se tiene conocimiento del esquema del almacén de datos (estructura subyacente).

## <a name="syntax"></a>Sintaxis

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="members"></a>Members

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|Recupera la información de la columna.|
|[GetXMLRowData](#getxmlrowdata)|Recupera todo el contenido de una tabla por filas.|

## <a name="remarks"></a>Observaciones

Sin embargo, `CXMLAccessor` difiere de `CDynamicStringAccessorW` en que convierte todos los datos a los que se tiene acceso desde el almacén de datos como datos con formato XML. Esto es especialmente útil para la salida a páginas web que reconocen XML. Los nombres de las etiquetas XML coincidirán con los nombres de columna del almacén de datos lo más cerca posible.

Use métodos `CDynamicAccessor` para obtener información de columnas. Esta información de columna se usa para crear un descriptor de acceso dinámicamente en tiempo de ejecución.

La información de la columna se almacena en un búfer creado y administrado por esta clase. Obtener información de columna mediante [GetXMLColumnData](#getxmlcolumndata) u obtener datos de columna por filas mediante [GetXMLRowData](#getxmlrowdata).

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="cxmlaccessorgetxmlcolumndata"></a><a name="getxmlcolumndata"></a>CXMLAccessor:: GetXMLColumnData

Recupera la información de tipo de columna de una tabla como datos de cadena con formato XML, por columna.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>Parámetros

*strOutput*<br/>
enuncia Referencia a un búfer de cadena que contiene la información de tipo de columna que se va a recuperar. Se aplica formato a la cadena con nombres de etiqueta XML que coinciden con los nombres de columna del almacén de datos.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

A continuación se muestra cómo se da formato a la información de tipo de columna en XML. `type` especifica el tipo de datos de la columna. Tenga en cuenta que los tipos de datos se basan en OLE DB tipos de datos, no en los de la base de datos a la que se tiene acceso.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="cxmlaccessorgetxmlrowdata"></a><a name="getxmlrowdata"></a>CXMLAccessor:: GetXMLRowData

Recupera todo el contenido de una tabla como datos de cadena con formato XML, por fila.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput,
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>Parámetros

*strOutput*<br/>
enuncia Referencia a un búfer que contiene los datos de la tabla que se van a recuperar. Los datos tienen el formato de datos de cadena con nombres de etiqueta XML que coinciden con los nombres de columna del almacén de datos.

*bAppend*<br/>
de Valor booleano que especifica si se va a anexar una cadena al final de los datos de salida.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Observaciones

A continuación se muestra cómo se da formato a los datos de fila en XML. `DATA` a continuación representa los datos de la fila. Utilice los métodos Move para moverse a la fila deseada.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>Consulte también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor (Clase)](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA (Clase)](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW (Clase)](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)
