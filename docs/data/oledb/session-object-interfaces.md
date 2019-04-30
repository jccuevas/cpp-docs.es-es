---
title: Interfaces del objeto de sesión
ms.date: 11/19/2018
helpviewer_keywords:
- session objects [OLE DB]
- session objects [OLE DB], interfaces
- OLE DB provider templates, object interfaces
- interfaces, session object
- interfaces, list of
ms.assetid: ac01a958-6dde-4bd7-8b63-94459e488335
ms.openlocfilehash: 2fb91365fec0709e1bb2a26afa519e6565862681
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62404587"
---
# <a name="session-object-interfaces"></a>Interfaces del objeto de sesión

En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de sesión.

|Interfaz|¿Obligatorio?|¿Implementado por plantillas OLE DB?|
|---------------|---------------|--------------------------------------|
|[IGetDataSource](/previous-versions/windows/desktop/ms709721(v=vs.85))|Obligatorio|Sí|
|[IOpenRowset](/previous-versions/windows/desktop/ms716946(v=vs.85))|Obligatorio|Sí|
|[ISessionProperties](/previous-versions/windows/desktop/ms713721(v=vs.85))|Obligatorio|Sí|
|[IAlterIndex](/previous-versions/windows/desktop/ms714943(v=vs.85))|Optional|No|
|[IAlterTable](/previous-versions/windows/desktop/ms719764(v=vs.85))|Optional|No|
|[IBindResource](/previous-versions/windows/desktop/ms714936(v=vs.85))|Optional|No|
|[ICreateRow](/previous-versions/windows/desktop/ms716832(v=vs.85))|Optional|No|
|[IDBCreateCommand](/previous-versions/windows/desktop/ms711625(v=vs.85))|Optional|Sí|
|[IDBSchemaRowset](/previous-versions/windows/desktop/ms713686(v=vs.85))|Optional|Sí|
|[IIndexDefinition](/previous-versions/windows/desktop/ms711593(v=vs.85))|Optional|No|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|Sí|
|[ITableCreation](/previous-versions/windows/desktop/ms713639(v=vs.85))|Optional|No|
|[ITableDefinition](/previous-versions/windows/desktop/ms714277(v=vs.85))|Optional|No|
|[ITableDefinitionWithConstraints](/previous-versions/windows/desktop/ms720947(v=vs.85))|Optional|No|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Optional|No|
|[ITransactionJoin](/previous-versions/windows/desktop/ms718071(v=vs.85))|Optional|No|
|[ITransactionLocal](/previous-versions/windows/desktop/ms714893(v=vs.85))|Optional|No|
|[ITransactionObject](/previous-versions/windows/desktop/ms713659(v=vs.85))|Optional|No|

El objeto de sesión crea un objeto de conjunto de filas. Si el proveedor admite comandos, la sesión también crea un objeto de comando (`CCommand`, implementación de OLE DB `TCommand`). El objeto de comando implementa la `ICommand` interfaz y se usa el `ICommand::Execute` método para ejecutar comandos en el conjunto de filas, como se muestra en la ilustración siguiente.

![Diagrama conceptual de proveedor](../../data/oledb/media/vc4u551.gif "diagrama conceptual de proveedor")

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
