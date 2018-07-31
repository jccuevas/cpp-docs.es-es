---
title: Interfaces del objeto Session | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 01d08fb35a1e954aad07153f63ad3ed34282570d
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39337851"
---
# <a name="session-object-interfaces"></a>Interfaces del objeto de sesión
En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de sesión.  
  
|Interfaz|¿Obligatorio?|¿Implementado por plantillas OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](https://msdn.microsoft.com/library/ms709721.aspx)|Obligatorio|Sí|  
|[IOpenRowset](https://msdn.microsoft.com/library/ms716946.aspx)|Obligatorio|Sí|  
|[ISessionProperties](https://msdn.microsoft.com/library/ms713721.aspx)|Obligatorio|Sí|  
|[IAlterIndex](https://msdn.microsoft.com/library/ms714943.aspx)|Optional|No|  
|[IAlterTable](https://msdn.microsoft.com/library/ms719764.aspx)|Optional|No|  
|[IBindResource](https://msdn.microsoft.com/library/ms714936.aspx)|Optional|No|  
|[ICreateRow](https://msdn.microsoft.com/library/ms716832.aspx)|Optional|No|  
|[IDBCreateCommand](https://msdn.microsoft.com/library/ms711625.aspx)|Optional|Sí|  
|[IDBSchemaRowset](https://msdn.microsoft.com/library/ms713686.aspx)|Optional|Sí|  
|[IIndexDefinition](https://msdn.microsoft.com/library/ms711593.aspx)|Optional|No|  
|[ISupportErrorInfo](https://msdn.microsoft.com/library/ms715816.aspx)|Optional|Sí|  
|[ITableCreation](https://msdn.microsoft.com/library/ms713639.aspx)|Optional|No|  
|[ITableDefinition](https://msdn.microsoft.com/library/ms714277.aspx)|Optional|No|  
|[ITableDefinitionWithConstraints](https://msdn.microsoft.com/library/ms720947.aspx)|Optional|No|  
|[ITransaction](https://msdn.microsoft.com/library/ms723053.aspx)|Optional|No|  
|[ITransactionJoin](https://msdn.microsoft.com/library/ms718071.aspx)|Optional|No|  
|[ITransactionLocal](https://msdn.microsoft.com/library/ms714893.aspx)|Optional|No|  
|[ITransactionObject](https://msdn.microsoft.com/library/ms713659.aspx)|Optional|No|  
  
 El objeto de sesión crea un objeto de conjunto de filas. Si el proveedor admite comandos, la sesión también crea un objeto de comando (`CCommand`, implementación de OLE DB `TCommand`). El objeto de comando implementa la `ICommand` interfaz y se usa el `ICommand::Execute` método para ejecutar comandos en el conjunto de filas, como se muestra en la ilustración siguiente.  
  
 ![Diagrama conceptual de proveedor](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)