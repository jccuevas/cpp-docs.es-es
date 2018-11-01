---
title: CDynamicStringAccessorA (Clase)
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorA
helpviewer_keywords:
- CDynamicStringAccessorA class
ms.assetid: ed0d9821-a655-41f1-a902-43c3042ac49c
ms.openlocfilehash: bfe4cf2d6aa107c21ed0d8b226616ebaa8488102
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50537441"
---
# <a name="cdynamicstringaccessora-class"></a>CDynamicStringAccessorA (Clase)

Permite obtener acceso a un origen de datos cuando no tiene conocimiento del esquema de base de datos (estructura subyacente).

## <a name="syntax"></a>Sintaxis

```cpp
typedef CDynamicStringAccessorT<CHAR, DBTYPE_STR> CDynamicStringAccessorA;
```

## <a name="remarks"></a>Comentarios

Solicitan que el proveedor recupere todos los datos que se obtiene acceso desde el almacén de datos como datos de cadena, pero `CDynamicStringAccessor` los datos de cadena ANSI de solicitudes.

`CDynamicStringAccessorA` hereda `GetString` y `SetString` desde `CDynamicStringAccessor`. Cuando se usan estos métodos en un `CDynamicStringAccessorA` objeto, `BaseType` es **CHAR**.

## <a name="requirements"></a>Requisitos

**Encabezado**: atldbcli.h

## <a name="see-also"></a>Vea también

[Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)<br/>
[Referencia de plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-reference.md)<br/>
[CAccessor (Clase)](../../data/oledb/caccessor-class.md)<br/>
[CDynamicParameterAccessor (Clase)](../../data/oledb/cdynamicparameteraccessor-class.md)<br/>
[CManualAccessor (Clase)](../../data/oledb/cmanualaccessor-class.md)<br/>
[CDynamicAccessor (Clase)](../../data/oledb/cdynamicaccessor-class.md)<br/>
[CDynamicStringAccessor (Clase)](../../data/oledb/cdynamicstringaccessor-class.md)<br/>
