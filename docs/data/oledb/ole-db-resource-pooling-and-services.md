---
title: Servicios y agrupación de recursos OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- resource pooling [OLE DB], provider requirements
- OLE DB, resource pooling
- service providers [OLE DB]
- OLE DB services [OLE DB], provider requirements
- OLE DB services [OLE DB]
- OLE DB providers, resource pooling
ms.assetid: 360c36e2-25ae-4caf-8ee7-d4a6b6898f68
ms.openlocfilehash: 67eeffff2bf165a5ccbdbaa546ad5b9ca9a57914
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210033"
---
# <a name="ole-db-resource-pooling-and-services"></a>Servicios y agrupación de recursos OLE DB

Para que funcione bien con la agrupación de OLE DB o con cualquier servicio OLE DB, el proveedor debe admitir la agregación de todos los objetos. Se trata de un requisito de cualquier proveedor OLE DB 1,5 o posterior. Es fundamental para aprovechar los servicios. Los proveedores que no admiten la agregación no se pueden agrupar y no se proporcionan servicios adicionales.

Para que se puedan agrupar, los proveedores deben admitir el modelo de subproceso libre. El grupo de recursos determina el modelo de subproceso del proveedor según la propiedad DBPROP_THREADMODEL.

Si el proveedor tiene un estado de conexión global que puede cambiar mientras el origen de datos está en un estado inicializado, debe admitir la nueva propiedad DBPROP_RESETDATASOURCE. Se llama a esta propiedad antes de que se vuelva a usar una conexión y se proporciona al proveedor la oportunidad de limpiar el estado antes de su siguiente uso. Si el proveedor no puede limpiar algún Estado asociado a la conexión, puede devolver DBPROPSTATUS_NOTSETTABLE para la propiedad y la conexión no se volverá a usar.

Los proveedores que se conectan a una base de datos remota y pueden detectar si esa conexión podría perderse deben admitir la propiedad DBPROP_CONNECTIONSTATUS. Esta propiedad proporciona a los OLE DB servicios la capacidad de detectar conexiones inactivas y asegurarse de que no se devuelven al grupo.

Por último, por lo general, la inscripción automática de transacciones no funcionará a menos que se implemente en el mismo nivel que la agrupación. Los proveedores que admiten la inscripción automática de transacciones deben admitir la deshabilitación de esta inscripción al exponer la propiedad DBPROP_INIT_OLEDBSERVICES y deshabilitar la inscripción si se anula la selección del DBPROPVAL_OS_TXNENLISTMENT.

## <a name="see-also"></a>Consulte también

[Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)
