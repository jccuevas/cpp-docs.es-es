---
title: "Agregar un controlador de mensajes ATL | Microsoft Docs"
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
  - "ATL, controladores de mensajes"
  - "ATL, ventanas"
  - "message handlers [C++]"
  - "message handling [C++], ATL message handler"
  - "windows [C++], ATL"
ms.assetid: cdea38a1-0d9b-4f8d-bbd5-b4f063fb3eeb
caps.latest.revision: 10
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Agregar un controlador de mensajes ATL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para agregar un controlador de mensajes \(miembro funciona que los mensajes de Windows de identificadores\) a un control, seleccione primero el control en la vista de clases.  A continuación se abre la ventana de **Propiedades** , seleccione el icono de **Mensajes** , y haga clic en el control desplegable del cuadro opuesta de mensaje requerido.  Esto agregará una declaración para el controlador de mensajes en una implementación básica de control el archivo de encabezado y de controlador en el archivo de .cpp del control.  También agregará el mapa de mensajes y agregará una entrada para el controlador.  
  
 Agregar un controlador de mensajes en ATL es similar a agregar un controlador de mensajes a una clase MFC.  Vea [Agregar un controlador de mensajes MFC](../mfc/reference/adding-an-mfc-message-handler.md) para obtener más información.  
  
 Las condiciones siguientes se aplican sólo a agregar un controlador de mensajes ATL:  
  
-   los controladores de mensajes siguen a la misma convención de nomenclatura que MFC.  
  
-   Las nuevas entradas del mapa de mensajes se agregan en el mapa principal de mensajes.  El asistente no reconoce mapas alternativos y encadenamiento de mensaje.  
  
## Vea también  
 [Implementing a Window](../atl/implementing-a-window.md)