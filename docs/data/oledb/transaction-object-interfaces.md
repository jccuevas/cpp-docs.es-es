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
ms.openlocfilehash: b86064c162dcacfbbc5877614c63d92d0f2bd347
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544535"
---
# <a name="transaction-object-interfaces"></a>Interfaces del objeto de transacción

El objeto de transacción define una unidad atómica de trabajo en un origen de datos y determina cómo se relacionan entre sí esas unidades de trabajo. Este objeto no es compatible directamente con las plantillas de proveedor de OLE DB (es decir, debe crear su propio objeto).

En la tabla siguiente se muestran las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de transacción.

|Interfaz|¿Necesario?|¿Se implementa mediante plantillas OLE DB?|
|---------------|---------------|--------------------------------------|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Mandatory|No|
|[ITransaction](/previous-versions/windows/desktop/ms723053(v=vs.85))|Mandatory|No|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Opcional|No|

## <a name="see-also"></a>Consulte también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
