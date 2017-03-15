---
title: "Consumidores y proveedores OLE DB | Microsoft Docs"
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
  - "consumidores OLE DB"
  - "consumidores OLE DB, arquitectura de datos OLE DB"
  - "proveedores OLE DB"
  - "proveedores OLE DB, arquitectura de datos OLE DB"
  - "OLE DB, modelo de datos"
ms.assetid: 886cb39d-652b-4557-93f0-4b1b0754d8bc
caps.latest.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Consumidores y proveedores OLE DB
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La arquitectura OLE DB usa el modelo de consumidores y proveedores.  Un consumidor efectúa solicitudes de datos.  Un proveedor responde a esas solicitudes colocando los datos en formato tabular y devolviéndolos al consumidor.  Cualquier llamada que haga el consumidor debe estar implementada en el proveedor.  
  
 Definido técnicamente, un consumidor es cualquier sistema o código de aplicación \(no necesariamente un componente de OLE DB\) que tiene acceso a datos por medio de interfaces de OLE DB.  Las interfaces se implementan en un proveedor.  Así, un proveedor es cualquier componente de software que implementa interfaces OLE DB para encapsular el acceso a los datos y exponerlos a otros objetos \(esto es, los consumidores\).  
  
 En términos de roles, un consumidor llama a los métodos de interfaces OLE DB; un proveedor OLE DB implementa las interfaces OLE DB necesarias.  
  
 OLE DB evita los términos cliente y servidor porque estos roles no siempre tienen sentido, en especial en situaciones de n\-niveles.  Un consumidor puede ser un componente en un nivel que sirve a otro componente, por lo que llamarlo componente cliente sería confuso.  Por otro lado, un proveedor a veces actúa más como un controlador de base de datos que como servidor.  
  
## Vea también  
 [Programación de OLE DB](../../data/oledb/ole-db-programming.md)   
 [Información general sobre la programación de OLE DB](../../data/oledb/ole-db-programming-overview.md)