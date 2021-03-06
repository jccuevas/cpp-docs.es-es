---
title: CDynamicStringAccessorW (Clase)
ms.date: 11/04/2016
f1_keywords:
- CDynamicStringAccessorW
helpviewer_keywords:
- CDynamicStringAccessorW class
ms.assetid: 9b7fd5cc-3a9b-4b57-b907-f1e35de2c98f
ms.openlocfilehash: 20ea4a2d795108e00c4b11c3abea6cf7b9953ca7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62230793"
---
# <a name="cdynamicstringaccessorw-class"></a>CDynamicStringAccessorW (Clase)

Permite obtener acceso a un origen de datos cuando no tiene conocimiento del esquema de base de datos (estructura subyacente).

## <a name="syntax"></a>Sintaxis

```cpp
typedef CDynamicStringAccessorT<WCHAR, DBTYPE_WSTR> CDynamicStringAccessorW;
```

## <a name="remarks"></a>Comentarios

Solicitan que el proveedor recupere todos los datos que se obtiene acceso desde el almacén de datos como datos de cadena, pero `CDynamicStringAccessor` solicita datos de cadena Unicode.

`CDynamicStringAccessorW` hereda `GetString` y `SetString` desde `CDynamicStringAccessor`. Cuando se usan estos métodos en un `CDynamicStringAccessorW` objeto, `BaseType` es **WCHAR**.

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
