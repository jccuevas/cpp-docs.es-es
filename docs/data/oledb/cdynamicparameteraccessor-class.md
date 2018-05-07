---
title: CDynamicParameterAccessor (clase) | Documentos de Microsoft
ms.custom: ''
ms.date: 02/14/2018
ms.technology:
- cpp-data
ms.topic: reference
f1_keywords:
- ATL.CDynamicParameterAccessor
- ATL::CDynamicParameterAccessor
- CDynamicParameterAccessor
dev_langs:
- C++
helpviewer_keywords:
- CDynamicParameterAccessor class
ms.assetid: 5f22626e-e80d-491f-8b3b-cedc50331960
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1b9478a5b2cc2190219ce2b297d1908683577c9e
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="cdynamicparameteraccessor-class"></a>CDynamicParameterAccessor (clase)

Similar a [CDynamicAccessor](../../data/oledb/cdynamicaccessor-class.md) pero obtiene la información de parámetros que puede establecer mediante una llamada a la [ICommandWithParameters](/sql/relational-databases/native-client-ole-db-interfaces/icommandwithparameters) interfaz.

## <a name="syntax"></a>Sintaxis

```cpp
class CDynamicParameterAccessor : public CDynamicAccessor
```

## <a name="members"></a>Miembros

### <a name="methods"></a>Métodos

|||
|-|-|
|[CDynamicParameterAccessor](../../data/oledb/cdynamicparameteraccessor-cdynamicparameteraccessor.md)|El constructor.|
|[GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md)|Recupera los datos de parámetros del búfer.|
|[GetParamCount](../../data/oledb/cdynamicparameteraccessor-getparamcount.md)|Recupera el número de parámetros en el descriptor de acceso.|
|[GetParamIO](../../data/oledb/cdynamicparameteraccessor-getparamio.md)|Determina si el parámetro especificado es un parámetro de entrada o salida.|
|[GetParamLength](../../data/oledb/cdynamicparameteraccessor-getparamlength.md)|Recupera la longitud del parámetro especificado almacenado en el búfer.|
|[GetParamName](../../data/oledb/cdynamicparameteraccessor-getparamname.md)|Recupera el nombre de un parámetro especificado.|
|[GetParamStatus](../../data/oledb/cdynamicparameteraccessor-getparamstatus.md)|Recupera el estado del parámetro especificado almacenado en el búfer.|
|[GetParamString](../../data/oledb/cdynamicparameteraccessor-getparamstring.md)|Recupera los datos de cadena del parámetro especificado almacenado en el búfer.|
|[GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md)|Recupera el tipo de datos de un parámetro especificado.|
|[SetParam](../../data/oledb/cdynamicparameteraccessor-setparam.md)|Establece el búfer con los datos de parámetros.|
|[SetParamLength](../../data/oledb/cdynamicparameteraccessor-setparamlength.md)|Establece la longitud del parámetro especificado almacenado en el búfer.|
|[SetParamStatus](../../data/oledb/cdynamicparameteraccessor-setparamstatus.md)|Establece el estado del parámetro especificado almacenado en el búfer.|
|[SetParamString](../../data/oledb/cdynamicparameteraccessor-setparamstring.md)|Establece los datos de cadena del parámetro especificado almacenado en el búfer.|

## <a name="remarks"></a>Comentarios

El proveedor debe admitir `ICommandWithParameters` para que el consumidor pueda usar esta clase.

La información de parámetros se almacena en un búfer creado y administrado por esta clase. Obtenga los datos de parámetros que están en el búfer mediante [GetParam](../../data/oledb/cdynamicparameteraccessor-getparam.md) y [GetParamType](../../data/oledb/cdynamicparameteraccessor-getparamtype.md).

Para obtener un ejemplo que muestra cómo utilizar esta clase para ejecutar un procedimiento almacenado de SQL Server y obtener los valores de parámetro de salida, vea el [DynamicConsumer](https://github.com/Microsoft/VCSamples/tree/master/VC2008Samples/ATL/OLEDB/Consumer/DynamicConsumer) ejemplo de código en el [Microsoft VCSamples](https://github.com/Microsoft/VCSamples) repositorio en GitHub.

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)  
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)  
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)  
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)  
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)  
