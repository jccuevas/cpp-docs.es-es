---
title: "Asignar mensajes a funciones | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.mapping.msg.function"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "mapas de mensajes [C++], asignar mensajes a funciones"
  - "mensajes de Windows [C++], agregar controladores de mensajes"
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Asignar mensajes a funciones
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La ventana Propiedades permite enlazar controladores de mensajes \(funciones miembro de clases MFC de interfaz de usuario\) con los mensajes generados por los recursos de su aplicación.  Utilizan [mapas de mensajes MFC](../../mfc/messages-and-commands-in-the-framework.md) para crear el enlace.  
  
 Al usar la Vista de clases para crear una nueva clase derivada de una de las clases del marco de trabajo, coloca automáticamente una clase completa y funcional en los archivos de encabezado \(.h\) e implementación \(.cpp\) que especifique.  
  
> [!NOTE]
>  Para agregar una nueva clase que no controle mensajes, cree la clase directamente en el editor de texto.  
  
### Para definir o quitar un controlador de mensajes mediante la ventana Propiedades  
  
1.  En la Vista de clases, haga clic en la clase.  
  
2.  En la ventana Propiedades, haga clic en el botón **Mensajes**.  
  
    > [!NOTE]
    >  El botón **Mensajes** está disponible al seleccionar el nombre de la clase en la Vista de clases o al hacer clic dentro de la ventana de código fuente.  
  
     Si el proyecto contiene un controlador para un mensaje, su nombre aparece en la columna derecha junto a éste.  
  
3.  Si el mensaje no tiene un controlador, haga clic en la celda en la columna derecha en la ventana Propiedades para mostrar el nombre sugerido de controlador como \<addHandlerName\>. \(Por ejemplo, el controlador de mensajes `WM_TIMER` sugiere \<agrega\>`OnTimer`\).  
  
4.  Haga clic en el nombre sugerido para agregar código auxiliar a la función.  
  
5.  Para modificar un controlador de mensajes, haga doble clic en el mensaje en la Vista de clases y modifique el código correspondiente en la ventana de código.  
  
 Para quitar un controlador de mensajes, un doble clic el controlador en la columna derecha y un deleteHandlerName seleccione\>\<.  El código de la función queda convertido en comentarios.  
  
## Vea también  
 [Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Adding Event Handlers for Dialog Box Controls](../../mfc/adding-event-handlers-for-dialog-box-controls.md)   
 [Explorar la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)