---
title: Interfaces del objeto de conjunto de filas | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
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
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: e8a1a5f5256087a8869426489fe01250b16fc598
ms.sourcegitcommit: 889a75be1232817150be1e0e8d4d7f48f5993af2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/30/2018
ms.locfileid: "39340516"
---
# <a name="rowset-object-interfaces"></a>Interfaces del objeto de conjunto de filas
En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de conjunto de filas.  
  
|Interfaz|¿Obligatorio?|¿Implementado por plantillas OLE DB?|  
|---------------|---------------|--------------------------------------|  
|[IAccessor](https://msdn.microsoft.com/library/ms719672.aspx)|Obligatorio|Sí|  
|[IColumnsInfo](https://msdn.microsoft.com/library/ms724541.aspx)|Obligatorio|Sí|  
|[IConvertType](https://msdn.microsoft.com/library/ms715926.aspx)|Obligatorio|Sí|  
|[IRowset](https://msdn.microsoft.com/library/ms720986.aspx)|Obligatorio|Sí|  
|[IRowsetInfo](https://msdn.microsoft.com/library/ms724541.aspx)|Obligatorio|Sí|  
|[IChapteredRowset](https://msdn.microsoft.com/library/ms718180.aspx)|Optional|No|  
|[IColumnsInfo2](https://msdn.microsoft.com/library/ms712953.aspx)|Optional|No|  
|[IColumnsRowset](https://msdn.microsoft.com/library/ms722657.aspx)|Optional|No|  
|[IConnectionPointContainer](http://msdn.microsoft.com/library/windows/desktop/ms683857)|Optional|Sí (mediante ATL)|  
|[IDBAsynchStatus](https://msdn.microsoft.com/library/ms709832.aspx)|Optional|No|  
|[IGetRow](https://msdn.microsoft.com/library/ms718047.aspx)|Optional|No|  
|[IRowsetChange](https://msdn.microsoft.com/library/ms715790.aspx)|Optional|Sí|  
|[IRowsetChapterMember](https://msdn.microsoft.com/library/ms725430.aspx)|Optional|No|  
|[IRowsetCurrentIndex](https://msdn.microsoft.com/library/ms709700.aspx)|Optional|No|  
|[IRowsetFind](https://msdn.microsoft.com/library/ms724221.aspx)|Optional|No|  
|[IRowsetIdentity](https://msdn.microsoft.com/library/ms715913.aspx)|Opcional (pero es obligatorio para los proveedores de nivel 0)|Sí|  
|[IRowsetIndex](https://msdn.microsoft.com/library/ms719604.aspx)|Optional|No|  
|[IRowsetLocate](https://msdn.microsoft.com/library/ms721190.aspx)|Optional|Sí|  
|[IRowsetRefresh](https://msdn.microsoft.com/library/ms714892.aspx)|Optional|No|  
|[IRowsetScroll](https://msdn.microsoft.com/library/ms712984.aspx)|Optional|No|  
|[IRowsetUpdate](https://msdn.microsoft.com/library/ms714401.aspx)|Optional|Sí|  
|[IRowsetView](https://msdn.microsoft.com/library/ms709755.aspx)|Optional|No|  
|[ISupportErrorInfo](https://msdn.microsoft.com/library/ms715816.aspx)|Optional|Sí|  
|[IRowsetBookmark](https://msdn.microsoft.com/library/ms714246.aspx)|Optional|No|  
  
 El objeto de conjunto de filas generados por el asistente implementa `IAccessor`, `IRowset`, y `IRowsetInfo` mediante herencia. El `IAccessorImpl` enlaza las dos columnas de salida. El `IRowset` controla la interfaz de recuperaciones de filas y datos. El `IRowsetInfo` interfaz controla las propiedades del conjunto de filas.  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)