---
title: Mapas de propiedades
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 174108cac9982e46a62a90f8cb60662527812e47
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575505"
---
# <a name="property-maps"></a>Mapas de propiedades

Con la sesión, el conjunto de filas y el objeto de comando opcional, cada proveedor admite una o varias propiedades. Estas propiedades se definen en las asignaciones de propiedad almacenados en los archivos de encabezado creados por el **Asistente para proveedores OLE DB**. Cada archivo de encabezado contiene una asignación para las propiedades en el grupo de propiedades de OLE DB definido para el objeto u objetos definidos en ese archivo. El archivo de encabezado que contiene el objeto de origen de datos también contiene el mapa de propiedades para el [propiedades DataSource](https://msdn.microsoft.com/library/ms724188). `Session.h` contiene la asignación de propiedad para el [propiedades de la sesión](/previous-versions/windows/desktop/ms714221). Los objetos de conjunto de filas y los comandos están en un archivo de encabezado único, denominado *projectname*RS.h. Estas propiedades son miembros de la [las propiedades del conjunto de filas](/previous-versions/windows/desktop/ms711252) grupo.

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
