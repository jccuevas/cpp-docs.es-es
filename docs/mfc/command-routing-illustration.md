---
title: "Ilustraci&#243;n de enrutamiento de comandos | Microsoft Docs"
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
  - "control de comandos, comandos de enrutamiento"
  - "enrutamiento de comandos, OnCmdMsg (controlador)"
  - "MFC, enrutamiento de comandos"
ms.assetid: 4b7b4741-565f-4878-b076-fd85c670f87f
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Ilustraci&#243;n de enrutamiento de comandos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para mostrar, considere un mensaje de comando de un elemento de menú claro Todo en el menú Edición de una aplicación MDI.  Supongamos que la función controladora para este comando resulta ser una función miembro de clase de la aplicación.  Aquí es cómo ese comando alcanza su controlador después de que el usuario elija el elemento de menú:  
  
1.  La ventana de marco principal recibe el mensaje de comando primero.  
  
2.  La ventana principal de marco MDI proporciona actualmente a ventana secundaria de MDI activa la oportunidad de controlar el comando.  
  
3.  El enrutamiento estándar de una ventana secundaria de MDI proporciona a la vista oportunidad en el comando antes de comprobar su propio mapa de mensajes.  
  
4.  La vista comprueba su propio mensaje asignado primero y, no encontrando ningún controlador, las siguientes rutas el comando al documento asociado.  
  
5.  El documento comprueba el mapa de mensajes y encuentra un controlador.  Esta función se denomina miembro de documentos y el enrutamiento detiene.  
  
 Si el documento no tuviera un controlador, distribuiría el comando a la plantilla de documento.  El comando volvería a la vista y después a la ventana de marco.  Finalmente, la ventana de marco comprueba el mapa de mensajes.  Si fallara esa comprobación también, distribuirían el comando de nuevo a la ventana principal de marco MDI y después al objeto application — el destino final de comandos no controlado.  
  
## Vea también  
 [Cómo el marco llama a un controlador](../mfc/how-the-framework-calls-a-handler.md)