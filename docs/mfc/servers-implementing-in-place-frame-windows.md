---
title: "Servidores: Implementar ventanas de marco en contexto | Microsoft Docs"
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
  - "ventanas de marco, implementar"
  - "ventanas de marco, en contexto"
  - "ventanas de marco en contexto"
  - "aplicaciones de servidor OLE, ventanas de marco"
  - "servidores, ventanas de marco en contexto"
ms.assetid: 09bde4d8-15e2-4fba-8d14-9b954d926b92
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Servidores: Implementar ventanas de marco en contexto
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

En este artículo se explica lo que debe hacer para implementar las ventanas en el contexto del cuadro de la aplicación de servidor de edición visual si no utiliza el asistente para aplicaciones para crear la aplicación de servidor.  En lugar de seguir el procedimiento antes en este caso, podría utilizar una clase de contexto existente de la cuadro\- ventana de una aplicación asistente\- generó la aplicación o un ejemplo proporcionado Visual C\+\+.  
  
#### Para declarar una clase de contexto de la cuadro\- ventana  
  
1.  Derive una clase de contexto de la cuadro\- ventana de `COleIPFrameWnd`.  
  
    -   Utilice la macro de `DECLARE_DYNCREATE` en el archivo de encabezado de clase.  
  
    -   Utilice la macro de `IMPLEMENT_DYNCREATE` en el archivo de implementación de la clase \(.cpp\).  Esto permite que los objetos de esta clase son creados por el marco.  
  
2.  Declarar un miembro de `COleResizeBar` en la clase de la cuadro\- ventana.  Esto es necesario si desea admitir el tamaño en contexto en aplicaciones de servidor.  
  
     Declare un controlador de mensajes `OnCreate` \(en la ventana de **Propiedades** \), y llame a **crear** para el miembro de `COleResizeBar` , si se ha definido.  
  
3.  Si tiene una barra de herramientas, declarar un miembro de `CToolBar` en la clase de la cuadro\- ventana.  
  
     Reemplace la función miembro de `OnCreateControlBars` para crear una barra de herramientas cuando el servidor está en contexto activo.  Por ejemplo:  
  
     [!code-cpp[NVC_MFCOleServer#1](../mfc/codesnippet/CPP/servers-implementing-in-place-frame-windows_1.cpp)]  
  
     Vea la explicación de este código después del paso 5.  
  
4.  Incluya el archivo de encabezado para esta clase de contexto de la cuadro\- ventana en el archivo principal .cpp.  
  
5.  En `InitInstance` para la clase de aplicación, llame a la función de `SetServerInfo` del objeto de plantilla de documento para especificar los recursos y la ventana en el contexto del cuadro que se utilizarán en abierto y edición en contexto.  
  
 La ejecución de llamadas de función en la instrucción de **if** crea la barra de herramientas de los recursos que el servidor proporcionada.  En este punto, la barra de herramientas es parte de la jerarquía de la ventana contenedora.  Dado que esta barra de herramientas se deriva de `CToolBar`, pasar los mensajes al propietario, la ventana cuadro de la aplicación contenedora, a menos que se cambie el propietario.  Por eso la llamada a `SetOwner` es necesaria.  Esta llamada cambia la ventana donde envían comandos de ser la ventana en el contexto del cuadro del servidor, haciendo que los mensajes que se pasarán al servidor.  Esto permite que el servidor reaccione a las operaciones en la barra de herramientas que proporciona.  
  
 El identificador del mapa de bits de la barra de herramientas debe ser igual que los demás recursos en contexto definidos en la aplicación de servidor.  Vea [Menús y recursos: Adiciones de Servidor](../mfc/menus-and-resources-server-additions.md) para obtener detalles.  
  
 Para obtener más información, vea [COleIPFrameWnd](../mfc/reference/coleipframewnd-class.md), [COleResizeBar](../mfc/reference/coleresizebar-class.md), y [CDocTemplate::SetServerInfo](../Topic/CDocTemplate::SetServerInfo.md) en *la referencia de la biblioteca de clases*.  
  
## Vea también  
 [Servidores](../mfc/servers.md)   
 [Servidores: Implementar un servidor](../mfc/servers-implementing-a-server.md)   
 [Servidores: Implementar documentos de servidor](../mfc/servers-implementing-server-documents.md)   
 [Servidores: Elementos de servidor](../mfc/servers-server-items.md)