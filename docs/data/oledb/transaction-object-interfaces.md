---
title: Interfaces del objeto de transacción | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- interfaces, OLE DB
- transaction object interfaces
- OLE DB, interfaces
- OLE DB providers, transaction support
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: d2ce99ce-6f7a-4ff9-bc6e-acda3633d5c8
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: b2d84d9a072d3eeaa84246a6692487be5c71679c
ms.sourcegitcommit: a41c4d096afca1e9b619bbbce045b77135d32ae2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/14/2018
ms.locfileid: "42572205"
---
# <a name="transaction-object-interfaces"></a>Interfaces del objeto de transacción
El objeto de transacción define una unidad atómica de trabajo en un origen de datos y determina cómo se relacionan entre sí las unidades de trabajo. Este objeto no es compatible directamente con las plantillas de proveedor OLE DB (es decir, debe crear su propio objeto).  
  
 En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de transacción.  
  
|Interfaz|¿Obligatorio?|¿Implementado por plantillas OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Obligatorio|No|  
|[ITransaction](/previous-versions/windows/desktop/ms723053\(v=vs.85\))|Obligatorio|No|  
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816\(v=vs.85\))|Optional|No|  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)