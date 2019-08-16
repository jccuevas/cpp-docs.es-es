---
title: Habilitar y deshabilitar servicios OLE DB
ms.date: 10/29/2018
helpviewer_keywords:
- OLE DB services [OLE DB], enabling and disabling
- service providers [OLE DB]
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
ms.openlocfilehash: df17a55950b03d4d63dea2199e3bc19bedb8a7e3
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62175347"
---
# <a name="enabling-and-disabling-ole-db-services"></a>Habilitar y deshabilitar servicios OLE DB

El Administrador de componentes de servicio de OLE DB compara las propiedades especificadas por el consumidor con las propiedades admitidas por el proveedor para determinar si los componentes individuales de servicio podrían utilizarse para cumplir con funcionalidad ampliada solicitada por el consumidor. Por ejemplo, si una aplicación solicita un cursor desplazable y el proveedor solo admite un cursor de solo avance, el Administrador de componentes de servicio utiliza el componente de servicio de motor de Cursor de cliente para proporcionar funcionalidad desplazable. Si la aplicación depende de funcionalidad ampliada admitida de forma predeterminada en el conjunto de filas del proveedor y la aplicación no establece explícitamente las propiedades para solicitar que la funcionalidad, la funcionalidad que no aparezcan en el conjunto de filas devuelto por el cliente Motor de cursor. Para ser interoperable, las aplicaciones siempre deben establecer las propiedades para solicitar explícitamente la funcionalidad ampliada donde sea necesario.

En algunos casos, podría ser necesario deshabilitar servicios OLE DB individuales para funcionar bien con las aplicaciones existentes que hacen suposiciones acerca de las características de un proveedor. Servicios OLE DB proporcionan la capacidad para deshabilitar los servicios individuales, o todos los servicios, ya sea en una conexión por conexión o para todas las aplicaciones mediante un único proveedor.

## <a name="see-also"></a>Vea también

[Servicios y agrupación de recursos OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)