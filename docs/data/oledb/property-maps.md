---
title: Mapas de propiedades
ms.date: 10/24/2018
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
ms.openlocfilehash: 9df98dc85c9242693319542cea0730341d87a052
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62284038"
---
# <a name="property-maps"></a>Mapas de propiedades

Con la sesión, el conjunto de filas y el objeto de comando opcional, cada proveedor admite una o varias propiedades. Estas propiedades se definen en las asignaciones de propiedad almacenados en los archivos de encabezado creados por el **Asistente para proveedores OLE DB**. Cada archivo de encabezado contiene una asignación para las propiedades en el grupo de propiedades de OLE DB definido para el objeto u objetos definidos en ese archivo. El archivo de encabezado que contiene el objeto de origen de datos también contiene el mapa de propiedades para el [propiedades DataSource](https://msdn.microsoft.com/library/ms724188). `Session.h` contiene la asignación de propiedad para el [propiedades de la sesión](/previous-versions/windows/desktop/ms714221(v=vs.85)). Los objetos de conjunto de filas y los comandos están en un archivo de encabezado único, denominado *projectname*RS.h. Estas propiedades son miembros de la [las propiedades del conjunto de filas](/previous-versions/windows/desktop/ms711252(v=vs.85)) grupo.

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
