---
title: "Archivos generados por el Asistente para proveedores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "proveedores OLE DB, archivos generados por el asistente"
ms.assetid: 6e1ac94b-eb90-4abf-82b3-06944b947ebc
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Archivos generados por el Asistente para proveedores
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El Asistente para proveedores OLE DB ATL genera los siguientes archivos.  En los temas siguientes se utiliza el nombre corto "MyProvider", pero los nombres exactos de los archivos dependen de la opción que elija al crear el proveedor.  
  
|Nombre de archivo|Descripción|  
|-----------------------|-----------------|  
|MyProviderRS.cpp|Contiene el método auxiliar `Execute` para comandos y el mapa de columnas del proveedor.|  
|MyProviderDS.h|Implementa el objeto de origen de datos.  Este archivo de encabezado contiene el mapa de propiedades para las propiedades del origen de datos.|  
|MyProviderDS.h|Implementa los objetos de comando y de conjunto de filas.  Este archivo de encabezado contiene el mapa de propiedades para las propiedades del conjunto de filas y del comando.|  
|MyProviderSess.h|Implementa el objeto de sesión.  Este archivo de encabezado contiene el mapa de propiedades para las propiedades de la sesión.|  
|MyProviderDS.h|Contiene los objetos registrados generados por el Asistente para proveedores OLE DB.|  
  
## Vea también  
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)