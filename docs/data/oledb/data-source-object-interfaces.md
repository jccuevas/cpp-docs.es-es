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
ms.openlocfilehash: a615694a9db75cdaf3b187cf6d29248bd26ef978
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544607"
---
# <a name="data-source-object-interfaces"></a>Interfaces del objeto de origen de datos

En la tabla siguiente se muestran las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de origen de datos.

|Interfaz|¿Necesario?|¿Se implementa mediante plantillas OLE DB?|
|---------------|---------------|--------------------------------------|
|`IDBCreateSession`|Mandatory|Sí|
|`IDBInitialize`|Mandatory|Sí|
|`IDBProperties`|Mandatory|Sí|
|[IPersist](/windows/win32/api/objidl/nn-objidl-ipersist)|Mandatory|Sí|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Opcional|No|
|`IDBDataSourceAdmin`|Opcional|No|
|`IDBInfo`|Opcional|No|
|[IPersistFile](/windows/win32/api/objidl/nn-objidl-ipersistfile)|Opcional|No|
|`ISupportErrorInfo`|Opcional|No|

El objeto de origen de datos implementa las interfaces `IDBProperties`, `IDBInitialize`y `IDBCreateSession` a través de la herencia. Puede optar por admitir funcionalidad adicional heredando o no heredando de una de estas clases de implementación. Si desea admitir la interfaz `IDBDataSourceAdmin`, debe heredar de la clase `IDBDataSourceAdminImpl`.

## <a name="see-also"></a>Consulte también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
