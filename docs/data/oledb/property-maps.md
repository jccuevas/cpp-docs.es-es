---
title: Mapas de propiedades | Microsoft Docs
ms.custom: ''
ms.date: 10/24/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 2c6c3ddc4b19cd9b65203d8a5e675b9ed75720a1
ms.sourcegitcommit: 840033ddcfab51543072604ccd5656fc6d4a5d3a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/29/2018
ms.locfileid: "50216466"
---
# <a name="property-maps"></a>Mapas de propiedades

Con la sesión, el conjunto de filas y el objeto de comando opcional, cada proveedor admite una o varias propiedades. Estas propiedades se definen en las asignaciones de propiedad almacenados en los archivos de encabezado creados por el **Asistente para proveedores OLE DB**. Cada archivo de encabezado contiene una asignación para las propiedades en el grupo de propiedades de OLE DB definido para el objeto u objetos definidos en ese archivo. El archivo de encabezado que contiene el objeto de origen de datos también contiene el mapa de propiedades para el [propiedades DataSource](https://msdn.microsoft.com/library/ms724188). `Session.h` contiene la asignación de propiedad para el [propiedades de la sesión](/previous-versions/windows/desktop/ms714221). Los objetos de conjunto de filas y los comandos están en un archivo de encabezado único, denominado *projectname*RS.h. Estas propiedades son miembros de la [las propiedades del conjunto de filas](/previous-versions/windows/desktop/ms711252) grupo.

## <a name="see-also"></a>Vea también

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)<br/>
