---
title: Interfaces del objeto Session | Documentos de Microsoft
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
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 71ac196508fc5b5054015bdc161476b75af2a598
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="session-object-interfaces"></a>Interfaces del objeto de sesión
En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de sesión.  
  
|Interfaz|¿Obligatorio?|¿Se implementan mediante plantillas OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IGetDataSource](https://msdn.microsoft.com/en-us/library/ms709721.aspx)|Obligatorio|Sí|  
|[IOpenRowset](https://msdn.microsoft.com/en-us/library/ms716946.aspx)|Obligatorio|Sí|  
|[ISessionProperties](https://msdn.microsoft.com/en-us/library/ms713721.aspx)|Obligatorio|Sí|  
|[IAlterIndex](https://msdn.microsoft.com/en-us/library/ms714943.aspx)|Optional|No|  
|[IAlterTable](https://msdn.microsoft.com/en-us/library/ms719764.aspx)|Optional|No|  
|[IBindResource](https://msdn.microsoft.com/en-us/library/ms714936.aspx)|Optional|No|  
|[ICreateRow](https://msdn.microsoft.com/en-us/library/ms716832.aspx)|Optional|No|  
|[IDBCreateCommand](https://msdn.microsoft.com/en-us/library/ms711625.aspx)|Optional|Sí|  
|[IDBSchemaRowset](https://msdn.microsoft.com/en-us/library/ms713686.aspx)|Optional|Sí|  
|[IIndexDefinition](https://msdn.microsoft.com/en-us/library/ms711593.aspx)|Optional|No|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Optional|Sí|  
|[ITableCreation](https://msdn.microsoft.com/en-us/library/ms713639.aspx)|Optional|No|  
|[ITableDefinition](https://msdn.microsoft.com/en-us/library/ms714277.aspx)|Optional|No|  
|[ITableDefinitionWithConstraints](https://msdn.microsoft.com/en-us/library/ms720947.aspx)|Optional|No|  
|[ITransaction](https://msdn.microsoft.com/en-us/library/ms723053.aspx)|Optional|No|  
|[ITransactionJoin](https://msdn.microsoft.com/en-us/library/ms718071.aspx)|Optional|No|  
|[ITransactionLocal](https://msdn.microsoft.com/en-us/library/ms714893.aspx)|Optional|No|  
|[ITransactionObject](https://msdn.microsoft.com/en-us/library/ms713659.aspx)|Optional|No|  
  
 El objeto de sesión crea un objeto de conjunto de filas. Si el proveedor admite comandos, la sesión también crea un objeto de comando (`CCommand`, implementar OLE DB **TCommand**). El objeto de comando implementa la `ICommand` interfaz y se utiliza el `ICommand::Execute` método para ejecutar comandos en el conjunto de filas, como se muestra en la ilustración siguiente.  
  
 ![Diagrama conceptual de proveedor](../../data/oledb/media/vc4u551.gif "vc4u551")  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)