---
title: Interfaces del objeto de conjunto de filas | Documentos de Microsoft
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
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 211fb5bbd0a950eff5f954d1c23b3dc993badb0d
ms.sourcegitcommit: d51ed21ab2b434535f5c1d553b22e432073e1478
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 02/23/2018
---
# <a name="rowset-object-interfaces"></a>Interfaces del objeto de conjunto de filas
En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de conjunto de filas.  
  
|Interfaz|¿Obligatorio?|¿Se implementan mediante plantillas OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IAccessor](https://msdn.microsoft.com/en-us/library/ms719672.aspx)|Obligatorio|Sí|  
|[IColumnsInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx)|Obligatorio|Sí|  
|[IConvertType](https://msdn.microsoft.com/en-us/library/ms715926.aspx)|Obligatorio|Sí|  
|[IRowset](https://msdn.microsoft.com/en-us/library/ms720986.aspx)|Obligatorio|Sí|  
|[IRowsetInfo](https://msdn.microsoft.com/en-us/library/ms724541.aspx)|Obligatorio|Sí|  
|[IChapteredRowset](https://msdn.microsoft.com/en-us/library/ms718180.aspx)|Optional|No|  
|[IColumnsInfo2](https://msdn.microsoft.com/en-us/library/ms712953.aspx)|Optional|No|  
|[IColumnsRowset](https://msdn.microsoft.com/en-us/library/ms722657.aspx)|Optional|No|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|Sí (a través de ATL)|  
|[IDBAsynchStatus](https://msdn.microsoft.com/en-us/library/ms709832.aspx)|Optional|No|  
|[IGetRow](https://msdn.microsoft.com/en-us/library/ms718047.aspx)|Optional|No|  
|[IRowsetChange](https://msdn.microsoft.com/en-us/library/ms715790.aspx)|Optional|Sí|  
|[IRowsetChapterMember](https://msdn.microsoft.com/en-us/library/ms725430.aspx)|Optional|No|  
|[IRowsetCurrentIndex](https://msdn.microsoft.com/en-us/library/ms709700.aspx)|Optional|No|  
|[IRowsetFind](https://msdn.microsoft.com/en-us/library/ms724221.aspx)|Optional|No|  
|[IRowsetIdentity](https://msdn.microsoft.com/en-us/library/ms715913.aspx)|Opcional (aunque obligatoria para proveedores de nivel 0)|Sí|  
|[IRowsetIndex](https://msdn.microsoft.com/en-us/library/ms719604.aspx)|Optional|No|  
|[IRowsetLocate](https://msdn.microsoft.com/en-us/library/ms721190.aspx)|Optional|Sí|  
|[IRowsetRefresh](https://msdn.microsoft.com/en-us/library/ms714892.aspx)|Optional|No|  
|[IRowsetScroll](https://msdn.microsoft.com/en-us/library/ms712984.aspx)|Optional|No|  
|[IRowsetUpdate](https://msdn.microsoft.com/en-us/library/ms714401.aspx)|Optional|Sí|  
|[IRowsetView](https://msdn.microsoft.com/en-us/library/ms709755.aspx)|Optional|No|  
|[ISupportErrorInfo](https://msdn.microsoft.com/en-us/library/ms715816.aspx)|Optional|Sí|  
|[IRowsetBookmark](https://msdn.microsoft.com/en-us/library/ms714246.aspx)|Optional|No|  
  
 El objeto de conjunto de filas generados por el asistente implementa `IAccessor`, `IRowset`, y `IRowsetInfo` a través de la herencia. El `IAccessorImpl` enlaza las dos columnas de salida. El `IRowset` interfaz controla recuperaciones de filas y los datos. El `IRowsetInfo` interfaz controla las propiedades del conjunto de filas.  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)