---
title: Interfaces del objeto de transacción
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
ms.openlocfilehash: 177f66222a054c3305418ffcd0acdda5c82ccf43
ms.sourcegitcommit: c40469825b6101baac87d43e5f4aed6df6b078f5
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/12/2018
ms.locfileid: "51556184"
---
# <a name="transaction-object-interfaces"></a>Interfaces del objeto de transacción

El objeto de transacción define una unidad atómica de trabajo en un origen de datos y determina cómo se relacionan entre sí las unidades de trabajo. Este objeto no es compatible directamente con las plantillas de proveedor OLE DB (es decir, debe crear su propio objeto).

En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de transacción.

|Interfaz|¿Obligatorio?|¿Implementado por plantillas OLE DB?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Obligatorio|No|
|[ITransaction](https://docs.microsoft.com/previous-versions/windows/desktop/ms723053(v=vs.85))|Obligatorio|No|
|[ISupportErrorInfo](https://docs.microsoft.com/previous-versions/windows/desktop/ms715816(v=vs.85))|Optional|No|

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
