---
title: Mapas de propiedades
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 79a65290c24ab016d9f81b54b9b7720d5c4ff352
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544559"
---
# <a name="property-maps"></a>Mapas de propiedades

Con la sesión, el conjunto de filas y el objeto de comando opcional, cada proveedor admite una o más propiedades. Estas propiedades se definen en las asignaciones de propiedades almacenadas en los archivos de encabezado creados por el **Asistente para proveedores de OLE DB**. Cada archivo de encabezado contiene una asignación para las propiedades del grupo de propiedades OLE DB definidas para el objeto o los objetos definidos en ese archivo. El archivo de encabezado que contiene el objeto de origen de datos también contiene la asignación de propiedad para las [propiedades de DataSource](/previous-versions/windows/desktop/ms724188(v=vs.85)). `Session.h` contiene el mapa de propiedades de las propiedades de la [sesión](/previous-versions/windows/desktop/ms714221(v=vs.85)). Los objetos de conjunto de filas y de comando se encuentran en un único archivo de encabezado, denominado *projectname*RS. h. Estas propiedades son miembros del grupo de [propiedades de conjunto de filas](/previous-versions/windows/desktop/ms711252(v=vs.85)) .

## <a name="see-also"></a>Consulte también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
