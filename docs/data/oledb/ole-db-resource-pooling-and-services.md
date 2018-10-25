---
title: OLE DB Resource Pooling y servicios | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: a90f60f830b4d5ec98685dbd8cd1c573d0fbcb4e
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50070301"
---
# <a name="ole-db-resource-pooling-and-services"></a>Servicios y agrupación de recursos OLE DB

Para que funcione bien con la agrupación de OLE DB, o con cualquier servicio de OLE DB, el proveedor debe admitir la agregación de todos los objetos. Se trata de un requisito de cualquier 1.5 de OLE DB o el proveedor de una versión posterior. Es fundamental para aprovechar los servicios. No se puede agrupar los proveedores que no admiten la agregación y no se proporciona sin ningún servicio.

Agrupar, los proveedores deben admitir el modelo de subprocesamiento libre. El grupo de recursos determina el modelo de subprocesos del proveedor según la `DBPROP_THREADMODEL` propiedad.

Si el proveedor tiene un estado de conexión global que puede cambiar mientras el origen de datos está en un estado inicializado, debe admitir los nuevos `DBPROP_RESETDATASOURCE` propiedad. Esta propiedad se llama antes de una conexión se vuelve a usar y ofrece al proveedor de la oportunidad de limpiar el estado antes de su uso siguiente. Si el proveedor no puede limpiar algún estado asociado a la conexión, puede devolver `DBPROPSTATUS_NOTSETTABLE` para la propiedad y la conexión no se reutilizará.

Los proveedores que se conectan a una base de datos remota y pueden detectar si la opción que se puede perder conexión debe admitir la `DBPROP_CONNECTIONSTATUS` propiedad. Esta propiedad proporciona la capacidad de detectar conexiones inactivas y asegúrese de que no se devuelven al grupo de los servicios de OLE DB.

Por último, la inscripción automática en transacciones no suele funciona a menos que se implementa en el mismo nivel que se produce la agrupación. Los proveedores que admiten la inscripción automática en transacciones deben admitir la deshabilitación mediante la exposición de la `DBPROP_INIT_OLEDBSERVICES` propiedad y deshabilitar la inscripción si el `DBPROPVAL_OS_TXNENLISTMENT` se anula la selección.

## <a name="see-also"></a>Vea también

[Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)