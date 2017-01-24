---
title: "Mapas de propiedades | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas, propiedad"
  - "proveedores OLE DB, propiedades"
  - "mapas de propiedades"
ms.assetid: 44abde56-90ad-4612-854e-d2fa5426fa80
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Mapas de propiedades
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Además de los objetos de sesión, de conjunto de filas y del objeto de comando opcional, cada proveedor admite una o más propiedades.  Estas propiedades se definen en mapas de propiedades contenidos en los archivos de encabezado creados por el Asistente para proveedores OLE DB.  Cada archivo de encabezado contiene un mapa para las propiedades en el grupo de propiedades OLE DB definido para el objeto u objetos definidos en ese archivo.  El archivo de encabezado que contiene el objeto de origen de datos también contiene el mapa de propiedades para las [propiedades de DataSource](https://msdn.microsoft.com/en-us/library/ms724188\(v=vs.140\).aspx).  Session.h contiene el mapa de propiedades de las [propiedades de Session](https://msdn.microsoft.com/en-us/library/ms714221.aspx).  Los objetos Rowset y Command residen en un único archivo de encabezado, denominado *projectname*RS.h.  Estas propiedades son miembros del grupo de [propiedades de Rowset](https://msdn.microsoft.com/en-us/library/ms711252.aspx).  
  
## Vea también  
 [Arquitectura de plantillas de proveedores OLE DB](../../data/oledb/ole-db-provider-template-architecture.md)