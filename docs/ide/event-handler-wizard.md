---
title: "Asistente para controladores de eventos | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.eventhandler.overview"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Asistente para controladores de eventos [C++]"
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Asistente para controladores de eventos
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Este asistente le agregará a una clase de su elección un controlador de eventos para un control de cuadro de diálogo.  Si agrega un controlador de eventos desde la [ventana Propiedades](../Topic/Properties%20Window.md), sólo podrá agregarlo a la clase que implemente el cuadro de diálogo.  Vea [Agregar controladores de eventos para controles de cuadros de diálogo](../mfc/adding-event-handlers-for-dialog-box-controls.md) para obtener más información.  
  
 **Nombre de comando**  
 Identifica el control seleccionado para el que se agrega el controlador de eventos.  Este cuadro no estará disponible.  
  
 **Tipo de mensaje**  
 Muestra la lista de los posibles controladores de mensajes actuales para el control seleccionado.  
  
 **Nombre de controlador de funciones**  
 Muestra el nombre de la función que se agrega para controlar el evento.  De forma predeterminada, el nombre se basa en el tipo de mensaje y en el comando, precedido por "On".  Por ejemplo, para el botón denominado `IDC_BUTTON1`, el tipo de mensaje `BN_CLICKED` mostrará el nombre de controlador de funciones `OnBnClickedButton1`.  
  
 **Lista de clases**  
 Muestra las clases disponibles a las que se puede agregar un controlador de eventos.  La clase del cuadro de diálogo seleccionado se mostrará en rojo.  
  
 **Descripción del controlador**  
 Proporciona una descripción del elemento seleccionado en el cuadro **Tipo de mensaje**.  Este cuadro no estará disponible.  
  
 **Agregar y editar**  
 Agrega el controlador de mensajes a la clase o al objeto seleccionado y, a continuación, abre el editor de texto en la nueva función para que se pueda agregar el código de controlador de notificación del control.  
  
 **Editar código**  
 Abre el editor de texto en la función existente seleccionada para que pueda agregar o editar el código de controlador de notificación del control.  
  
## Vea también  
 [Agregar un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md)