---
title: CXMLAccessor (clase) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- CXMLAccessor class
- GetXMLColumnData method
- GetXMLRowData method
ms.assetid: c88c082c-ec2f-4351-8947-a330b15e448a
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 71922df2b4d94d06b21ade32b4d8c4ca22fa50c8
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50065426"
---
# <a name="cxmlaccessor-class"></a>CXMLAccessor (Clase)

Permite obtener acceso a orígenes de datos como datos de cadena cuando no tiene conocimiento del esquema del almacén de datos (estructura subyacente).

## <a name="syntax"></a>Sintaxis

```cpp
class CXMLAccessor : public CDynamicStringAccessorW
```

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[GetXMLColumnData](#getxmlcolumndata)|Recupera la información de columna.|
|[GetXMLRowData](#getxmlrowdata)|Recupera el contenido completo de una tabla por filas.|

## <a name="remarks"></a>Comentarios

Sin embargo, `CXMLAccessor` difiere `CDynamicStringAccessorW` en que lo convierte todos los datos que se obtiene acceso desde el almacén de datos como datos (etiquetados) en formato XML. Esto es especialmente útil para la salida a las páginas Web basadas en XML. Los nombres de etiqueta XML coincidirá con nombres de columna del almacén de datos lo más fielmente posible.

Use `CDynamicAccessor` métodos para obtener información de columna. Utilice esta información de columna para crear un descriptor de acceso de forma dinámica en tiempo de ejecución.

La información de columna se almacena en un búfer creado y administrado por esta clase. Obtener información de columna mediante [GetXMLColumnData](#getxmlcolumndata) u obtener datos de columna por filas mediante [GetXMLRowData](#getxmlrowdata).

## <a name="example"></a>Ejemplo

[!code-cpp[NVC_OLEDB_Consumer#14](../../data/oledb/codesnippet/cpp/cxmlaccessor-class_1.cpp)]

## <a name="getxmlcolumndata"></a> CXMLAccessor:: GetXMLColumnData

Recupera la información de tipo de columna de una tabla como datos de cadena en formato XML, por columna.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetXMLColumnData(CSimpleStringW& strOutput) throw();
```

#### <a name="parameters"></a>Parámetros

*strOutput*<br/>
[out] Una referencia a un búfer de cadena que contiene la información de tipo de columna va a recuperar. Formato de la cadena con los nombres de etiqueta XML que coinciden con los nombres de columna del almacén de datos.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

A continuación muestra cómo se da formato a la información de tipo de columna en XML. `type` Especifica el tipo de datos de la columna. Tenga en cuenta que los tipos de datos se basan en tipos de datos OLE DB, no los de la base de datos que se obtiene acceso.

`<columninfo>`

`<column type = I2/> ColumnName`

`</columninfo>`

## <a name="getxmlrowdata"></a> CXMLAccessor:: GetXMLRowData

Recupera todo el contenido de una tabla como datos de cadena en formato XML, por fila.

### <a name="syntax"></a>Sintaxis

```cpp
HRESULT GetXMLRowData(CSimpleStringW& strOutput, 
   bool bAppend = false) throw();
```

#### <a name="parameters"></a>Parámetros

*strOutput*<br/>
[out] Una referencia a un búfer que contiene los datos de la tabla va a recuperar. Formato de los datos como datos de cadena con los nombres de etiqueta XML que coinciden con los nombres de columna del almacén de datos.

*bAppend*<br/>
[in] Valor booleano que especifica si se deben anexar una cadena al final de los datos de salida.

### <a name="return-value"></a>Valor devuelto

Uno de los valores HRESULT estándar.

### <a name="remarks"></a>Comentarios

A continuación muestra cómo se da formato a la fila de datos en XML. `DATA` a continuación representa la fila de datos. Utilice move métodos para desplazarse a la fila deseada.

`<row>`

`<column name>DATA</column name>`

`</row>`

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)<br/>
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CDynamicStringAccessor (Clase)](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
[CDynamicStringAccessorA (Clase)](../../data/oledb/cdynamicstringaccessora-class.md)<br/>
[CDynamicStringAccessorW (Clase)](../../data/oledb/cdynamicstringaccessorw-class.md)<br/>
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)