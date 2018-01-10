---
title: Mapas de propiedades | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- OLE DB providers, properties
- maps, property
- property maps
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 05bd576e6e55c94306a8dd648c57a4d606bed696
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="property-maps"></a>Mapas de propiedades
Además de la sesión, el conjunto de filas y el objeto de comando opcional, cada proveedor admite una o varias propiedades. Estas propiedades se definen en asignaciones de propiedad que contiene los archivos de encabezado creados por el Asistente para proveedores OLE DB. Cada archivo de encabezado contiene un mapa para las propiedades en el grupo de propiedades de OLE DB definido para el objeto u objetos definidos en ese archivo. El archivo de encabezado que contiene el objeto de origen de datos también contiene la asignación de propiedad para el [propiedades de origen de datos](https://msdn.microsoft.com/en-us/library/ms724188\(v=vs.140\).aspx). Session.h contiene la asignación de propiedad para el [propiedades de la sesión](https://msdn.microsoft.com/en-us/library/ms714221.aspx). Los objetos rowset y command residen en un archivo de encabezado único, denominado *projectname*RS.h. Estas propiedades son miembros de la [propiedades de conjunto de filas](https://msdn.microsoft.com/en-us/library/ms711252.aspx) grupo.  
  
## <a name="see-also"></a>Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)