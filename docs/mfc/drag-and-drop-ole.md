---
title: "Arrastrar y colocar (OLE) | Microsoft Docs"
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
  - "arrastrar y colocar [C++]"
  - "arrastrar y colocar [C++], acerca de arrastrar y colocar en funciones OLE"
  - "compatibilidad con arrastrar y colocar el Administrador de archivos"
  - "OLE (aplicaciones), arrastrar y colocar"
  - "funciones OLE de arrastrar y colocar"
  - "aplicaciones de servidor OLE, arrastrar y colocar"
ms.assetid: a4595350-ca06-4400-88a1-f0175c76b77b
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Arrastrar y colocar (OLE)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La característica de arrastrar y colocar de OLE es principalmente un acceso directo para copiar y pegar datos.  Cuando se utiliza el portapapeles para copiar o pegar datos, son necesarios varios pasos.  Selecciona los datos, haga clic en **Cortado** o **copiar** de menú de **edición** , desplácese al archivo de destino, la ventana o la aplicación, coloque el cursor en la ubicación deseada, y haga clic en **Pegar** de menú de **edición** .  
  
 La operación de arrastrar y colocar de OLE es diferente del mecanismo de arrastrar y colocar del administrador de archivos, que controla los nombres de archivo y se ha diseñado específicamente pasar los nombres de archivo a las aplicaciones.  La operación de arrastrar y colocar de OLE es mucho más general.  Le permite arrastrar y colocar los datos que se podría poner en el portapapeles.  
  
 Cuando se utiliza el método de arrastrar y colocar de OLE, quita dos pasos del proceso.  Selecciona los datos de la ventana de código fuente \(“el origen de colocación”\), la arrastra el destino deseado \(“destino”\), y colóquelo lanzar el botón del mouse.  La operación elimina la necesidad de menús y es más rápida que la secuencia de copias\/pegar.  El único requisito es que el origen de colocación y el destino deben estar abierto y al menos parcialmente visible en la pantalla.  
  
 Mediante el método de arrastrar y colocar de OLE, los datos se pueden transferir desde una ubicación a otra dentro de un documento, entre diferentes documentos, o entre aplicaciones.  Se puede implementar en un contenedor o una aplicación de servidor, y cualquier aplicación puede ser un origen de colocación, un destino, o ambas.  Si una aplicación tiene el origen de colocación y compatibilidad de destino implementados, la operación de arrastrar y colocar está habilitada entre ventanas secundarias, o dentro de una ventana.  Esta característica puede crear la aplicación mucho más fácil de utilizar.  
  
 Si solo desea usar la funcionalidad de arrastrar y colocar de OLE, vea [Arrastrar y colocar: El personalizar](../mfc/drag-and-drop-customizing.md).  Puede usar las técnicas explicadas en ese caso para crear orígenes de posición de las aplicaciones de no OLE.  El artículo [Arrastrar y colocar: Implementar un destino](../mfc/drag-and-drop-implementing-a-drop-target.md) describe cómo implementar la compatibilidad de destino para las aplicaciones VIEJAS y de no OLE.  También se útil examinar los ejemplos [OCLIENT](../top/visual-cpp-samples.md) y [HIERSVR](../top/visual-cpp-samples.md)MFC OLE.  
  
 Si no ha leído la familia de [Objetos de datos y orígenes de datos \(OLE\)](../mfc/data-objects-and-data-sources-ole.md) de casos, puede ser tan ahora hacer.  Estos casos explican los fundamentos de la transferencia de datos, y cómo implementarla en las aplicaciones.  
  
 Para obtener más información acerca de arrastrar y colocar, vea:  
  
-   [Arrastrar y colocar: Implementar un origen de colocación](../mfc/drag-and-drop-implementing-a-drop-source.md)  
  
-   [Arrastrar y colocar: Implementar un destino](../mfc/drag-and-drop-implementing-a-drop-target.md)  
  
-   [Arrastrar y colocar: El personalizar](../mfc/drag-and-drop-customizing.md)  
  
## Vea también  
 [OLE](../mfc/ole-in-mfc.md)   
 [Objetos de datos y orígenes de datos \(OLE\)](../mfc/data-objects-and-data-sources-ole.md)