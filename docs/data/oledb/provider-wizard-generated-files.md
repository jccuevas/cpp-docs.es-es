---
title: Archivos generados por el Asistente para proveedores | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, wizard-generated files
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 26e20e0417e2253158930a8d3d055171fe767001
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46108409"
---
# <a name="provider-wizard-generated-files"></a>Archivos generados por el Asistente para proveedores

El Asistente para proveedores OLE DB ATL genera los siguientes archivos. Los temas siguientes utilizan el nombre corto "MyProvider", pero los nombres de archivo exacto dependen de la elección realizada cuando se crea el proveedor.  
  
|Nombre del archivo|Descripción|  
|---------------|-----------------|  
|MyProviderRS.cpp|Contiene la aplicación auxiliar de comando `Execute` método y el mapa de columnas del proveedor.|  
|MyProviderDS.h|Implementa el objeto de origen de datos. Este archivo de encabezado contiene la asignación de propiedad para propiedades del origen de datos.|  
|MyProviderRS.h|Implementa los objetos de comando y conjunto de filas. Este archivo de encabezado contiene la asignación de propiedad para las propiedades del conjunto de filas y el comando.|  
|MyProviderSess.h|Implementa el objeto de sesión. Este archivo de encabezado contiene la asignación de propiedad para propiedades de la sesión.|  
|MyProvider.rgs|Contiene los objetos registrados generados por el Asistente para proveedores OLE DB.|  
  
## <a name="see-also"></a>Vea también  

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)