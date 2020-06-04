---
title: Interfaces del objeto Rowset
ms.date: 10/24/2018
helpviewer_keywords:
- interfaces, OLE DB
- OLE DB, interfaces
- rowset objects [OLE DB]
- OLE DB provider templates, object interfaces
- interfaces, list of
ms.assetid: 0d7a5d48-2fe4-434f-a84b-157c1fdc3494
ms.openlocfilehash: d9c2c61714a98d9de09d8657352a14f296e35a58
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544547"
---
# <a name="rowset-object-interfaces"></a>Interfaces del objeto Rowset

En la tabla siguiente se muestran las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de conjunto de filas.

|Interfaz|¿Necesario?|¿Se implementa mediante plantillas OLE DB?|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672(v=vs.85))|Mandatory|Sí|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Mandatory|Sí|
|[IConvertType](/previous-versions/windows/desktop/ms715926(v=vs.85))|Mandatory|Sí|
|[IRowset](/previous-versions/windows/desktop/ms720986(v=vs.85))|Mandatory|Sí|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541(v=vs.85))|Mandatory|Sí|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180(v=vs.85))|Opcional|No|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953(v=vs.85))|Opcional|No|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657(v=vs.85))|Opcional|No|
|[IConnectionPointContainer](/windows/win32/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Opcional|Sí (a través de ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832(v=vs.85))|Opcional|No|
|[IGetRow](/previous-versions/windows/desktop/ms718047(v=vs.85))|Opcional|No|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790(v=vs.85))|Opcional|Sí|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430(v=vs.85))|Opcional|No|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700(v=vs.85))|Opcional|No|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221(v=vs.85))|Opcional|No|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913(v=vs.85))|Opcional (pero necesario para los proveedores de nivel 0)|Sí|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604(v=vs.85))|Opcional|No|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190(v=vs.85))|Opcional|Sí|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892(v=vs.85))|Opcional|No|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984(v=vs.85))|Opcional|No|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401(v=vs.85))|Opcional|Sí|
|[IRowsetView](/previous-versions/windows/desktop/ms709755(v=vs.85))|Opcional|No|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816(v=vs.85))|Opcional|Sí|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246(v=vs.85))|Opcional|No|

El objeto de conjunto de filas generado por el asistente implementa `IAccessor`, `IRowset`y `IRowsetInfo` a través de la herencia. La `IAccessorImpl` enlaza ambas columnas de salida. La interfaz de `IRowset` controla las capturas de filas y datos. La interfaz `IRowsetInfo` controla las propiedades del conjunto de filas.

## <a name="see-also"></a>Consulte también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
