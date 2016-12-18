---
title: "Definir un controlador de mensajes para un mensaje reflejado | Microsoft Docs"
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
  - "vc.codewiz.defining.msg.msghandler"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "control de mensajes, mensajes reflejados"
  - "mensajes, reflejados"
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Definir un controlador de mensajes para un mensaje reflejado
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Una vez se haya creado una nueva clase de control MFC, se pueden definir sus controladores de mensajes correspondientes.  Los controladores de mensajes reflejados permiten a la clase del control controlar sus propios mensajes antes de que la ventana principal reciba el mensaje.  Se puede usar la función de MFC [CWnd::SendMessage](../Topic/CWnd::SendMessage.md) para enviar mensajes desde un control a una ventana principal.  
  
 Con esta funcionalidad es posible, por ejemplo, crear un cuadro de lista que se redibuje a sí mismo en lugar de confiar en que lo haga la ventana principal \(ventana propietaria\).  Para obtener más información sobre los mensajes reflejados, vea [Controlar mensajes reflejados](../../mfc/handling-reflected-messages.md).  
  
 Para crear un [control ActiveX](../../mfc/activex-controls-on-the-internet.md) con la misma funcionalidad, se debe crear un proyecto para el control.  
  
> [!NOTE]
>  No se puede agregar un mensaje reflejado \(OCM\_*Mensaje*\) para un control ActiveX mediante la ventana Propiedades, según se describe a continuación.  Se deben agregar dichos mensajes manualmente.  
  
### Para definir un controlador de mensajes para un mensaje reflejado desde la ventana Propiedades  
  
1.  Agregue un control, como una lista, un control Rebar, una barra de herramientas o un control de árbol al proyecto MFC.  
  
2.  En la Vista de clases, haga clic en el nombre de la clase del control.  
  
3.  En la [ventana Propiedades](../Topic/Properties%20Window.md), el nombre de la clase del control aparece en la lista **Nombre de clase**.  
  
4.  Haga clic en el botón **Mensajes** para mostrar los mensajes de Windows disponibles para agregar al control.  
  
5.  Desplácese hacia abajo en la lista de mensajes de la ventana Propiedades hasta que vea el encabezado **Reflejado.** Como alternativa, haga clic en el botón **Categorías** y contraiga la vista para ver el encabezado **Reflejado.**  
  
6.  Seleccione el mensaje reflejado para el cual desee definir un controlador.  Los mensajes reflejados aparecen señalados con el signo igual \(\=\).  
  
7.  Haga clic en la celda en la columna derecha en la ventana Propiedades para mostrar el nombre sugerido de controlador como \<addHandlerName\>. \(Por ejemplo, el controlador de mensajes **\=WM\_CTLCOLOR** sugiere \<agrega\>**CtlColor**\).  
  
8.  Haga clic en el nombre sugerido que desea aceptar.  Se agregará el controlador al proyecto.  
  
     Los nombres de controladores de mensajes agregados aparecerán en la columna derecha de la ventana de mensajes reflejados.  
  
9. Para editar o eliminar un controlador de mensajes, repita los pasos 4 a 7.  Haga clic en la celda que contiene el nombre del controlador que desea editar o eliminar y haga clic en la tarea apropiada.  
  
## Vea también  
 [Asignar mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)   
 [Agregar funcionalidad con los Asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes de MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Explorar la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)