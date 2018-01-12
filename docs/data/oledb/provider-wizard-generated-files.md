---
title: Archivos generados por el Asistente para proveedores | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords: OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 27fb95e5dc1c417d3dfb03217463a8ef683f3710
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="provider-wizard-generated-files"></a>Archivos generados por el Asistente para proveedores
El Asistente para proveedores OLE DB ATL genera los siguientes archivos. Los temas siguientes utiliza el nombre corto "MyProvider", pero los nombres de archivo exacto dependen de la elección realizada al crear el proveedor.  
  
|Nombre del archivo|Descripción|  
|---------------|-----------------|  
|MyProviderRS.cpp|Contiene la aplicación auxiliar de comando `Execute` método y el mapa de columnas del proveedor.|  
|MyProviderDS.h|Implementa el objeto de origen de datos. Este archivo de encabezado contiene la asignación de propiedad para las propiedades de origen de datos.|  
|: MyProviderRS.h|Implementa los objetos de comando y el conjunto de filas. Este archivo de encabezado contiene la asignación de propiedad para las propiedades de conjunto de filas y de comando.|  
|MyProviderSess.h|Implementa el objeto de sesión. Este archivo de encabezado contiene la asignación de propiedad para las propiedades de la sesión.|  
|MyProvider.rgs|Contiene los objetos registrados generados por el Asistente para proveedores OLE DB.|  
  
## <a name="see-also"></a>Vea también  
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)