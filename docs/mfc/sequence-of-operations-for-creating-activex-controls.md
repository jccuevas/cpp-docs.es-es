---
title: "Secuencia de operaciones para crear controles ActiveX | Microsoft Docs"
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
  - "controles ActiveX [C++], crear"
  - "controles ActiveX en MFC [C++], crear"
  - "controles OLE [C++], MFC"
  - "secuencia [C++]"
  - "secuencia [C++], para crear controles ActiveX"
ms.assetid: 7d868c53-a0af-4ef6-a89c-e1c03c583a53
caps.latest.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 7
---
# Secuencia de operaciones para crear controles ActiveX
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra el rol y el rol de marco en crear controles ActiveX \(anteriormente conocido como controles OLE\).  
  
### Crear Controles ActiveX  
  
|Tarea|Hace|Hace el marco|  
|-----------|----------|-------------------|  
|Cree un marco del control ActiveX.|Ejecute el asistente para controles ActiveX MFC para crear el control.  Especifique las opciones que desee en las páginas opciones.  Las opciones incluyen el tipo y el nombre del control en el proyecto, la autorización, crear subclases, y un método de cuadro Acerca de.|El asistente para controles ActiveX MFC crea los archivos de un control ActiveX con funcionalidad básica, incluidos los archivos de código fuente de la aplicación, el control, y la página de propiedades o páginas; un archivo de recursos; un archivo de proyecto; y otros, bien todo a las especificaciones.|  
|Vea lo que proporcionan el control y el asistente para controles ActiveX sin agregar una línea del propio código.|Compile el control ActiveX y pruébelo con Internet Explorer o [Ejemplo TSTCON](../top/visual-cpp-samples.md).|El control actual tiene la capacidad de cambiar de tamaño y de mover.  También tiene un método de **Cuadro Acerca de** \(si se elige\) que puede ser invocado.|  
|Implemente los métodos y propiedades de control.|Implemente los métodos y propiedades CONTROL\- específicos agregando funciones miembro para proporcionar una interfaz expuesta a los datos del control.  Agregue las variables miembro para contener las estructuras de datos y utilizar controladores de eventos para desencadenar eventos cuando se determina.|El marco ha definido un mapa para admitir los eventos del control, propiedades, y los métodos, permitiéndole para centrarse en cómo se implementan las propiedades y métodos.  La propiedad predeterminada es visible y se proporciona un método predeterminado del cuadro acerca de.|  
|Crear la página de propiedades o las páginas del control.|Usar los editores de recursos de Visual C\+\+ para editar visualmente la interfaz de la página de propiedades del control:<br /><br /> -   Crear páginas de propiedades adicionales.<br />-   Crear y editar los mapas de bits, iconos, y los cursores.<br /><br /> También puede probar la página de propiedades en el editor de cuadros de diálogo.|El archivo de recursos predeterminado creado por el Asistente para aplicaciones proporciona MFC muchos de los recursos que necesita.  Visual C\+\+ permite editar recursos existentes y agregar nuevos recursos con facilidad y visualmente.|  
|Pruebe los eventos, los métodos, y las propiedades del control.|Recompile el contenedor de prueba del control y de uso para probar que los controladores correctamente.|Puede llamar a los métodos de control y manipular sus propiedades a través de la interfaz de la página de propiedades o a través del contenedor de prueba.  Además, contenedor de prueba de uso a los eventos de seguimiento desencadenados de control y de las notificaciones recibidos por el contenedor del control.|  
  
## Vea también  
 [Compilar en el marco](../mfc/building-on-the-framework.md)   
 [Secuencia de operaciones para compilar aplicaciones MFC](../mfc/sequence-of-operations-for-building-mfc-applications.md)   
 [Secuencia de operaciones para crear aplicaciones OLE](../mfc/sequence-of-operations-for-creating-ole-applications.md)   
 [Secuencia de operaciones para crear aplicaciones de base de datos](../mfc/sequence-of-operations-for-creating-database-applications.md)