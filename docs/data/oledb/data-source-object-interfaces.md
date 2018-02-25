---
title: Interfaces del objeto de origen de datos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
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
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c0a045657b80ddaf70792d1c7f617b0e1f7c0b4a
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
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