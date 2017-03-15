---
title: "Habilitar y deshabilitar servicios OLE DB | Microsoft Docs"
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
  - "servicios OLE DB [OLE DB], habilitar y deshabilitar"
  - "proveedores de servicios [OLE DB]"
ms.assetid: 445f97eb-32a8-41c2-ad26-1169f78a074f
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Habilitar y deshabilitar servicios OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El Administrador de componentes de servicio de OLE DB compara las propiedades especificadas por el consumidor con las admitidas por el proveedor para determinar si es posible llamar a los componentes individuales de servicio para que satisfagan la funcionalidad ampliada solicitada por el consumidor.  Por ejemplo, si una aplicación solicita un cursor desplazable y el proveedor sólo admite un cursor de sólo avance, el Administrador de componentes de servicio invoca al componente del servicio Client Cursor Engine para proporcionar funcionalidad desplazable.  Si la aplicación se basa en funcionalidad ampliada admitida de manera predeterminada en el conjunto de filas del proveedor y la aplicación no establece explícitamente las propiedades para solicitar esa funcionalidad, puede que no aparezca esta funcionalidad en el conjunto de filas devuelto por Client Cursor Engine.  Para que haya interoperatividad, las aplicaciones siempre deben establecer valores de propiedades para solicitar explícitamente la funcionalidad que necesitan.  
  
 En algunos casos, puede ser necesario deshabilitar servicios OLE DB individuales para trabajar bien con las aplicaciones existentes que hacen suposiciones acerca de las características de un proveedor.  Los servicios OLE DB proporcionan la capacidad de deshabilitar servicios individuales, o todos los servicios, conexión a conexión o para todas las aplicaciones mediante un único proveedor.  
  
## Vea también  
 [Servicios y agrupación de recursos OLE DB](../../data/oledb/ole-db-resource-pooling-and-services.md)