---
title: "Tipos de mensajes asociados a objetos de la interfaz de usuario | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.uiobject.msgs"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "tipos de mensaje y objetos de interfaz de usuario"
ms.assetid: 681ee1a7-f6e6-4ea0-9fc6-1fb53a35516e
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipos de mensajes asociados a objetos de la interfaz de usuario
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La tabla siguiente muestra los tipos de objetos con los que se puede trabajar y los tipos de mensajes asociados a ellos.  
  
### Objetos de la interfaz de usuario y sus mensajes asociados  
  
|Id. de objeto|Mensajes|  
|-------------------|--------------|  
|Nombre de la clase, que representa la ventana contenedora|Mensajes de Windows apropiados para una clase derivada de [CWnd](../../mfc/reference/cwnd-class.md): un cuadro de diálogo, una ventana, una ventana secundaria, una ventana secundaria MDI o una ventana marco de nivel superior.|  
|Identificador de menú o tecla aceleradora|-   Mensaje **COMMAND** \(ejecuta la función del programa\).<br />-   Mensaje **UPDATE\_COMMAND\_UI** \(actualiza dinámicamente el elemento de menú\).|  
|Identificador de control|Mensajes de notificación de control para el tipo de control seleccionado.|  
  
## Vea también  
 [Asignar mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Explorar la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)