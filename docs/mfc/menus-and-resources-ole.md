---
title: "Men&#250;s y recursos (OLE) | Microsoft Docs"
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
  - "aplicaciones [OLE], menús y recursos"
  - "contenedores [C++], aplicaciones de contenedor OLE"
  - "activación en contexto, menús y recursos OLE"
  - "menús [C++], aplicaciones de documentos OLE"
  - "aplicaciones OLE [C++], menús y recursos"
  - "contenedores OLE, menús y recursos"
  - "menús y recursos OLE"
  - "aplicaciones de servidor OLE, menús y recursos"
  - "servidor de edición visual OLE"
  - "aplicaciones de servidor, menús y recursos OLE"
  - "barras de estado, aplicaciones de documentos OLE"
  - "edición de cadenas, aplicaciones de edición visual"
  - "tablas de cadenas, aplicaciones de edición visual"
  - "barras de herramientas [C++], aplicaciones de documentos OLE"
  - "edición visual, menús y recursos de la aplicación"
ms.assetid: 52bfa086-7d3d-466f-94c7-c7061f3bdb3a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Men&#250;s y recursos (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este grupo de casos explica el uso de menús y recursos en aplicaciones VIEJAS de documento de MFC.  
  
 Requisitos adicionales de los lugares visuales de OLE de edición en el menú y otros recursos proporcionados por aplicaciones VIEJAS de documento porque hay varios modos en los que las aplicaciones del contenedor y del servidor \(componente\) pueden ser iniciadas y utilizar.  Por ejemplo, una aplicación de completo\- Servidor se puede ejecutar en cualquiera de estos tres modos:  
  
-   Solo admiten.  
  
-   En su lugar, para editar un elemento en el contexto de un contenedor.  
  
-   Abrir, modificar un elemento fuera del contexto de su contenedor, en una ventana independiente.  
  
 Esto requiere tres diseños independientes de menú, uno para cada modo posible de la aplicación.  Las tablas de aceleradores también son necesarias para cada nuevo modo.  Una aplicación contenedora puede o no puede admitir la activación de contexto; si lo hace, necesita una nueva estructura de menú y tablas asociadas de aceleradores.  
  
 La activación de contexto requiere que el contenedor y las aplicaciones de servidor deben negociar para el menú, la barra de herramientas, y el espacio de la barra de estado.  Todos los recursos deben diseñarse con esta perspectiva.  El artículo [Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md) cubre este tema en detalle.  
  
 Debido a estos problemas, las aplicaciones VIEJAS de documento creadas con el asistente para aplicaciones pueden tener hasta cuatro menús y recursos distintos de la tabla de aceleradores.  Estos se utilizan por las razones siguientes:  
  
|Nombre del recurso|Utilice|  
|------------------------|-------------|  
|**IDR\_MAINFRAME**|Se utiliza en una aplicación MDI si no hay ningún archivo abierto, o en una aplicación SDI independientemente de los archivos abiertos.  Éste es el menú estándar para aplicaciones de no OLE.|  
|**IDR\_projectTYPE\<\>**|Se utiliza en una aplicación MDI si los archivos abiertos.  Se utiliza cuando una aplicación se ejecuta independiente.  Éste es el menú estándar para aplicaciones de no OLE.|  
|**\<\>IDR\_projectTYPE\_SRVR\_IP**|Utilizado por el servidor o el contenedor cuando un objeto está en el lugar abierto.|  
|**\<\>IDR\_projectTYPE\_SRVR\_EMB**|Utilizado por una aplicación de servidor si un objeto se abre sin utilizar la activación en contexto.|  
  
 Cada uno de estos nombres de recurso representa un menú y, normalmente, una tabla de aceleradores.  Un esquema similar se debe utilizar en las aplicaciones MFC que no se crean con el asistente para aplicaciones.  
  
 Los casos siguientes describen los temas relacionados con los contenedores, los servidores, y la combinación de menús necesaria para implementar la activación de contexto:  
  
-   [Menús y recursos: Adiciones de contenedor](../mfc/menus-and-resources-container-additions.md)  
  
-   [Menús y recursos: Adiciones de Servidor](../mfc/menus-and-resources-server-additions.md)  
  
-   [Menús y recursos: Combinación de menús](../mfc/menus-and-resources-menu-merging.md)  
  
## Vea también  
 [OLE](../mfc/ole-in-mfc.md)