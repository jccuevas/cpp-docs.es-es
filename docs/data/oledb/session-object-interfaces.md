---
title: Interfaces del objeto de sesión
ms.date: 10/24/2018
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
ms.openlocfilehash: 19a2830ba97038624072ce4d9b8eca573ddd7d28
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50588726"
---
# <a name="session-object-interfaces"></a>Interfaces del objeto de sesión

En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de sesión.

|Interfaz|¿Obligatorio?|¿Implementado por plantillas OLE DB?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](/previous-versions/windows/desktop/ms709721)|Obligatorio|Sí|
|[IOpenRowset](/previous-versions/windows/desktop/ms716946)|Obligatorio|Sí|
|[ISessionProperties](/previous-versions/windows/desktop/ms713721)|Obligatorio|Sí|
|[IAlterIndex](/previous-versions/windows/desktop/ms714943)|Optional|No|
|[IAlterTable](/previous-versions/windows/desktop/ms719764)|Optional|No|
|[IBindResource](/previous-versions/windows/desktop/ms714936)|Optional|No|
|[ICreateRow](/previous-versions/windows/desktop/ms716832)|Optional|No|
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625)|Optional|Sí|
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686)|Optional|Sí|
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593)|Optional|No|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|Optional|Sí|
|[ITableCreation](/previous-versions/windows/desktop/ms713639)|Optional|No|
|[ITableDefinition](/previous-versions/windows/desktop/ms714277)|Optional|No|
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947)|Optional|No|
|[ITransaction](/previous-versions/windows/desktop/ms723053)|Optional|No|
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071)|Optional|No|
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893)|Optional|No|
|[ITransactionObject](/previous-versions/windows/desktop/ms713659)|Optional|No|

El objeto de sesión crea un objeto de conjunto de filas. Si el proveedor admite comandos, la sesión también crea un objeto de comando (`CCommand`, implementación de OLE DB `TCommand`). El objeto de comando implementa la `ICommand` interfaz y se usa el `ICommand::Execute` método para ejecutar comandos en el conjunto de filas, como se muestra en la ilustración siguiente.

![Diagrama conceptual de proveedor](../../data/oledb/media/vc4u551.gif "vc4u551")

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
