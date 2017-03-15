---
title: "Servidores: Implementar un servidor | Microsoft Docs"
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
  - "aplicaciones de servidor OLE, implementar servidores OLE"
  - "servidores, implementar"
ms.assetid: 5bd57e8e-3b23-4f23-9597-496fac2d24b5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Servidores: Implementar un servidor
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica el código que el asistente para aplicaciones MFC crea para una aplicación de servidor de edición visual.  Si no está utilizando el asistente para aplicaciones, listas de este artículo las áreas donde debe escribir código para implementar una aplicación de servidor.  
  
 Si utiliza el asistente para aplicaciones para crear una aplicación de servidor, proporciona una cantidad significativa de código Servidor\- concreto para usted.  Si está agregando funcionalidad visual de servidor de edición en una aplicación existente, debe duplicar el código para que el asistente para aplicaciones habría proporcionado antes de agregar el resto del código de servidor necesario.  
  
 El código de servidor que el asistente para aplicaciones proporciona entra en varias categorías:  
  
-   Definición de recursos de servidor:  
  
    -   El recurso de menú utilizado cuando el servidor está editando un elemento incrustado en su propia ventana.  
  
    -   Recursos de menús y de la barra de herramientas utilizados cuando el servidor está en contexto activo.  
  
     Para obtener más información sobre estos recursos, vea [Menús y recursos: Adiciones de Servidor](../mfc/menus-and-resources-server-additions.md).  
  
-   Definir una clase de elemento derivada de `COleServerItem`.  Para obtener detalles adicionales en elementos de servidor, vea [Servidores: Elementos de Servidor](../mfc/servers-server-items.md).  
  
-   Cambiar la clase base de la clase del documento a `COleServerDoc`.  Para obtener más información, vea [Servidores: Implementar documentos de Servidor](../mfc/servers-implementing-server-documents.md).  
  
-   Definir una clase de la cuadro\- ventana derivada de `COleIPFrameWnd`.  Para obtener más información, vea [Servidores: Implementar el cuadro en contexto Windows](../mfc/servers-implementing-in-place-frame-windows.md).  
  
-   Crear una entrada para la aplicación de servidor en la base de datos del registro y registrar de Windows la nueva instancia del servidor con el sistema OLE.  Para obtener información sobre este tema, vea [Registro](../mfc/registration.md).  
  
-   Inicializar e iniciar la aplicación de servidor.  Para obtener información sobre este tema, vea [Registro](../mfc/registration.md).  
  
 Para obtener más información, vea [COleServerItem](../mfc/reference/coleserveritem-class.md), [COleServerDoc](../mfc/reference/coleserverdoc-class.md), y [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md) en *la referencia de la biblioteca de clases*.  
  
## Vea también  
 [Servidores](../mfc/servers.md)   
 [Contenedores](../mfc/containers.md)   
 [Menús y recursos \(OLE\)](../mfc/menus-and-resources-ole.md)   
 [Registro](../mfc/registration.md)