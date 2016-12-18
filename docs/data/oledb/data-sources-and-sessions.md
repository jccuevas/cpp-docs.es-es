---
title: "Or&#237;genes de datos y sesiones | Microsoft Docs"
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
  - "conexiones [C++], origen de datos"
  - "orígenes de datos [C++], OLE DB"
  - "plantillas de consumidor OLE DB [C++], orígenes de datos"
ms.assetid: 6ee52216-e082-4869-a1d6-ce561cfb76e5
caps.latest.revision: 10
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Or&#237;genes de datos y sesiones
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La ilustración siguiente muestra las clases que permiten conectar y obtener acceso a un origen de datos.  Cada clase está basada en una implementación de componente de OLE DB estándar.  
  
 ![Clases de origen de datos y sesión](../../data/oledb/media/vcdatasourcesessionclasses.png "vcDataSourceSessionClasses")  
Clases de origen de datos y sesión  
  
 Las clases son las siguientes:  
  
-   [CDataSource](../../data/oledb/cdatasource-class.md) Esta clase genera una instancia del objeto de origen de datos, que crea y administra una conexión a un origen de datos por medio de un proveedor OLE DB.  El origen de datos toma la información \(como la dirección del origen de datos y los datos de autenticación\) como una cadena de conexión.  
  
     También merece la pena resaltar que la clase auxiliar [CEnumerator](../../data/oledb/cenumerator-class.md) se suele usar antes de establecer una conexión para obtener una lista de los proveedores disponibles registrados en un sistema.  Ello permite seleccionar un proveedor como origen de datos.  Por ejemplo, el cuadro de diálogo **Propiedades de vínculo de datos** usa esta clase para llenar la lista de proveedores de la ficha **Proveedores**.  Equivale a las funciones **SQLBrowseConnect** o **SQLDriverConnect**.  
  
-   [CSession](../../data/oledb/csession-class.md) Esta clase crea una instancia del objeto de sesión, que representa una sesión única de acceso al origen de datos.  Sin embargo, se pueden crear varias sesiones en un origen de datos.  Por cada sesión, se pueden crear conjuntos de filas, comandos y otros objetos para obtener acceso a los datos que contiene el origen de datos.  La sesión controla las transacciones.  
  
## Vea también  
 [Plantillas de consumidor OLE DB](../../data/oledb/ole-db-consumer-templates-cpp.md)