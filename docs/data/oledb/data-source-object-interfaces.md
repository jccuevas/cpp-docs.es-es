---
title: Interfaces del objeto de origen de datos
ms.date: 10/24/2018
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
ms.openlocfilehash: aaa9e90996750b0518999803487fcb39729c76f9
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50519657"
---
# <a name="data-source-object-interfaces"></a>Interfaces del objeto de origen de datos

En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de origen de datos.

|Interfaz|¿Obligatorio?|¿Implementado por plantillas OLE DB?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|Obligatorio|Sí|
|`IDBInitialize`|Obligatorio|Sí|
|`IDBProperties`|Obligatorio|Sí|
|[IPersist](/windows/desktop/api/objidl/nn-objidl-ipersist)|Obligatorio|Sí|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|No|
|`IDBDataSourceAdmin`|Optional|No|
|`IDBInfo`|Optional|No|
|[IPersistFile](/windows/desktop/api/objidl/nn-objidl-ipersistfile)|Optional|No|
|`ISupportErrorInfo`|Optional|No|

Los datos del origen de objeto implementa la `IDBProperties`, `IDBInitialize`, y `IDBCreateSession` interfaces mediante herencia. Puede ofrecer funcionalidad adicional heredando o no de una de estas clases de implementación. Si desea admitir la `IDBDataSourceAdmin` interfaz, debe heredar de la `IDBDataSourceAdminImpl` clase.

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
