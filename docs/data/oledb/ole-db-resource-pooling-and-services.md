---
title: OLE DB agrupación de recursos y servicios | Documentos de Microsoft
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
ms.openlocfilehash: ab8c5e5a3e219da7204ef1a1b4942dc70b2f2ad2
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33111190"
---
# <a name="ole-db-resource-pooling-and-services"></a>Servicios y agrupación de recursos OLE DB
Para trabajar correctamente con la agrupación de OLE DB, o con cualquier servicio de OLE DB, el proveedor debe admitir la agregación de todos los objetos. Se trata de un requisito de OLE DB 1.5 o posterior proveedor. Es fundamental para aprovechar los servicios. No se puede agrupar los proveedores que no admiten la agregación y no hay servicios adicionales se proporcionan.  
  
 Para poder agruparlos, los proveedores deben admitir el modelo de subprocesamiento libre. El grupo de recursos determina el modelo del proveedor subproceso según la **DBPROP_THREADMODEL** propiedad.  
  
 Si el proveedor tiene un estado de conexión global que puede cambiar mientras el origen de datos está en un estado inicializado, debe admitir los nuevos **DBPROP_RESETDATASOURCE** propiedad. Esta propiedad se llama antes de que una conexión se reutiliza y proporciona al proveedor de la oportunidad de limpiar el estado antes de su uso siguiente. Si el proveedor no puede limpiar algún estado asociado a la conexión, puede devolver **DBPROPSTATUS_NOTSETTABLE** para la propiedad y la conexión no se reutilizará.  
  
 Los proveedores que se conectan a una base de datos remota y pueden detectar si la opción que podría perderse conexión debe admitir la **DBPROP_CONNECTIONSTATUS** propiedad. Esta propiedad proporciona a los servicios de OLE DB la capacidad de detectar conexiones inactivas y asegúrese de que no se devuelven al grupo.  
  
 Por último, la inscripción automática en transacciones no suele funciona a menos que se implementa en el mismo nivel que se produce la agrupación. Los proveedores que admiten la inscripción automática en transacciones deben admitir su deshabilitación mediante la exposición de la **DBPROP_INIT_OLEDBSERVICES** propiedad y deshabilitar la inscripción si la **DBPROPVAL_OS_ TXNENLISTMENT** se anule la selección.  
  
## <a name="see-also"></a>Vea también  
 [Técnicas avanzadas para proveedores](../../data/oledb/advanced-provider-techniques.md)