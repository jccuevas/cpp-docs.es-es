---
title: Habilitar y deshabilitar servicios OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: 3016126d09b39ec74f4acb758a2176be05052648
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80210969"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Habilitar y deshabilitar servicios OLE DB

El OLE DB administrador de componentes de servicio compara las propiedades especificadas por el consumidor con las propiedades admitidas por el proveedor para determinar si los componentes de servicio individuales se pueden usar para satisfacer la funcionalidad extendida solicitada por el consumidor. Por ejemplo, si una aplicación solicita un cursor desplazable y el proveedor solo admite un cursor de solo avance, el administrador de componentes de servicio utiliza el componente de servicio del motor de cursor de cliente para proporcionar funcionalidad desplazable. Si la aplicación se basa en la funcionalidad extendida admitida de forma predeterminada en el conjunto de filas del proveedor y la aplicación no establece explícitamente las propiedades para solicitar esa funcionalidad, es posible que la funcionalidad no aparezca en el conjunto de filas devuelto por el cliente. Motor de cursores. Para que sea interoperable, las aplicaciones siempre deben establecer propiedades para solicitar explícitamente la funcionalidad extendida cuando sea necesario.

En algunos casos, podría ser necesario deshabilitar los servicios de OLE DB individuales para que funcionen bien con las aplicaciones existentes que realizan suposiciones sobre las características de un proveedor. Los servicios de OLE DB proporcionan la capacidad de deshabilitar servicios individuales o de todos los servicios, ya sea por conexión o para todas las aplicaciones que usan un solo proveedor.

## <a name="see-also"></a>Consulte también

[Servicios y agrupación de recursos OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)
