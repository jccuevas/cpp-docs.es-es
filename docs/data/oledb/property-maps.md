---
title: Mapas de propiedades | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: b3fb9c5a5c18925bfcd448bb2349379262b27361
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46080992"
---
# <a name="property-maps"></a>Mapas de propiedades

Además de la sesión, el conjunto de filas y el objeto de comando opcional, cada proveedor admite una o varias propiedades. Estas propiedades se definen en asignaciones de propiedad que contiene los archivos de encabezado creados por el Asistente para proveedores OLE DB. Cada archivo de encabezado contiene una asignación para las propiedades en el grupo de propiedades de OLE DB definido para el objeto u objetos definidos en ese archivo. El archivo de encabezado que contiene el objeto de origen de datos también contiene el mapa de propiedades para el [propiedades DataSource](https://msdn.microsoft.com/library/ms724188\(v=vs.140\).aspx). Session.h contiene el mapa de propiedades para el [propiedades de la sesión](/previous-versions/windows/desktop/ms714221\(v=vs.85\)). Los objetos de conjunto de filas y el comando residen en un archivo de encabezado único, denominado *projectname*RS.h. Estas propiedades son miembros de la [las propiedades del conjunto de filas](/previous-versions/windows/desktop/ms711252\(v=vs.85\)) grupo.  
  
## <a name="see-also"></a>Vea también  

[Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)