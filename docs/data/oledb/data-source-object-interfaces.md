---
title: Interfaces del objeto de origen de datos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- data source objects [C++], interfaces
- data source objects [C++]
- interfaces [C++], OLE DB
- interfaces [C++], list of
- OLE DB provider templates [C++], object interfaces
- OLE DB [C++], interfaces
ms.assetid: 929e100c-c08c-4b64-8437-d8d1357226f6
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 1c8aaed0a9f50e20dba5938b9b37425f4caa2bb1
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33101882"
---
# <a name="data-source-object-interfaces"></a>Interfaces del objeto de origen de datos
En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de origen de datos.  
  
|Interfaz|¿Obligatorio?|¿Se implementan mediante plantillas OLE DB?|  
|---------------|---------------|--------------------------------------|  
|`IDBCreateSession`|Obligatorio|Sí|  
|`IDBInitialize`|Obligatorio|Sí|  
|`IDBProperties`|Obligatorio|Sí|  
|[IPersist](http://msdn.microsoft.com/library/windows/desktop/ms688695)|Obligatorio|Sí|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|No|  
|`IDBDataSourceAdmin`|Optional|No|  
|`IDBInfo`|Optional|No|  
|[IPersistFile](http://msdn.microsoft.com/library/windows/desktop/ms687223)|Optional|No|  
|`ISupportErrorInfo`|Optional|No|  
  
 Los datos del origen de objeto implementa la `IDBProperties`, `IDBInitialize`, y `IDBCreateSession` interfaces a través de la herencia. Puede elegir entre ofrecer funcionalidad adicional heredando o no heredando de una de estas clases de implementación. Si desea admitir la `IDBDataSourceAdmin` interfaz, debe heredar de la `IDBDataSourceAdminImpl` clase.  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)