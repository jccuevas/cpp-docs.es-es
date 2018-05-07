---
title: Habilitar y deshabilitar servicios OLE DB | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 785997cafec76bfa438382ace6930d53c31c4dc9
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="enabling-and-disabling-ole-db-services"></a>Habilitar y deshabilitar servicios OLE DB
El Administrador de componentes de servicio de OLE DB compara las propiedades especificadas por el consumidor para aquellos admitidos por el proveedor para determinar si se pudieron invocar componentes individuales de servicio para satisfacer la funcionalidad ampliada solicitada por el consumidor. Por ejemplo, si una aplicación solicita un cursor desplazable y el proveedor sólo admite un cursor de solo avance, el Administrador de componentes de servicio invoca al componente de servicio de motor de Cursor de cliente para proporcionar funcionalidad desplazable. Si la aplicación depende de funcionalidad extendida que se admiten de forma predeterminada en el conjunto de filas del proveedor y la aplicación no establece explícitamente las propiedades para solicitar que la funcionalidad, la funcionalidad que no aparezcan en el conjunto de filas devuelto por el cliente Motor de cursor. Para que sea interoperable, las aplicaciones siempre deben establecer propiedades para solicitar explícitamente la funcionalidad extendida cuando sea necesario.  
  
 En algunos casos, podría ser necesario deshabilitar servicios OLE DB individuales que funcionen bien con las aplicaciones existentes que hacen suposiciones acerca de las características de un proveedor. Servicios OLE DB proporcionan la capacidad de deshabilitar servicios individuales, o todos los servicios, ya sea en forma de conexión por conexión o para todas las aplicaciones mediante un único proveedor.  
  
## <a name="see-also"></a>Vea también  
 [Servicios y agrupación de recursos OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)