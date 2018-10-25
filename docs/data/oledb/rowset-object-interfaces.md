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
ms.openlocfilehash: 29371e1c1acff5846b7b2c454365f9ff52b77231
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50056937"
---
# <a name="rowset-object-interfaces"></a>Interfaces del objeto de conjunto de filas

En la tabla siguiente se muestra las interfaces obligatorias y opcionales definidas por OLE DB para un objeto de conjunto de filas.

|Interfaz|¿Obligatorio?|¿Implementado por plantillas OLE DB?|
|---------------|---------------|--------------------------------------|
|[IAccessor](/previous-versions/windows/desktop/ms719672)|Obligatorio|Sí|
|[IColumnsInfo](/previous-versions/windows/desktop/ms724541)|Obligatorio|Sí|
|[IConvertType](/previous-versions/windows/desktop/ms715926)|Obligatorio|Sí|
|[IRowset](/previous-versions/windows/desktop/ms720986)|Obligatorio|Sí|
|[IRowsetInfo](/previous-versions/windows/desktop/ms724541)|Obligatorio|Sí|
|[IChapteredRowset](/previous-versions/windows/desktop/ms718180)|Optional|No|
|[IColumnsInfo2](/previous-versions/windows/desktop/ms712953)|Optional|No|
|[IColumnsRowset](/previous-versions/windows/desktop/ms722657)|Optional|No|
|[IConnectionPointContainer](/windows/desktop/api/ocidl/nn-ocidl-iconnectionpointcontainer)|Optional|Sí (mediante ATL)|
|[IDBAsynchStatus](/previous-versions/windows/desktop/ms709832)|Optional|No|
|[IGetRow](/previous-versions/windows/desktop/ms718047)|Optional|No|
|[IRowsetChange](/previous-versions/windows/desktop/ms715790)|Optional|Sí|
|[IRowsetChapterMember](/previous-versions/windows/desktop/ms725430)|Optional|No|
|[IRowsetCurrentIndex](/previous-versions/windows/desktop/ms709700)|Optional|No|
|[IRowsetFind](/previous-versions/windows/desktop/ms724221)|Optional|No|
|[IRowsetIdentity](/previous-versions/windows/desktop/ms715913)|Opcional (pero es obligatorio para los proveedores de nivel 0)|Sí|
|[IRowsetIndex](/previous-versions/windows/desktop/ms719604)|Optional|No|
|[IRowsetLocate](/previous-versions/windows/desktop/ms721190)|Optional|Sí|
|[IRowsetRefresh](/previous-versions/windows/desktop/ms714892)|Optional|No|
|[IRowsetScroll](/previous-versions/windows/desktop/ms712984)|Optional|No|
|[IRowsetUpdate](/previous-versions/windows/desktop/ms714401)|Optional|Sí|
|[IRowsetView](/previous-versions/windows/desktop/ms709755)|Optional|No|
|[ISupportErrorInfo](/previous-versions/windows/desktop/ms715816)|Optional|Sí|
|[IRowsetBookmark](/previous-versions/windows/desktop/ms714246)|Optional|No|

El objeto de conjunto de filas generados por el asistente implementa `IAccessor`, `IRowset`, y `IRowsetInfo` mediante herencia. El `IAccessorImpl` enlaza las dos columnas de salida. El `IRowset` controla la interfaz de recuperaciones de filas y datos. El `IRowsetInfo` interfaz controla las propiedades del conjunto de filas.

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)