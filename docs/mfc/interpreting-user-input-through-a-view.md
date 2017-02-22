---
title: "Interpretar la entrada del usuario a trav&#233;s de una vista | Microsoft Docs"
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
  - "CView (clase), interpretar la entrada del usuario"
  - "entrada, clase de vista"
  - "interpretar la entrada del usuario a través de vistas"
  - "datos proporcionados por el usuario, interpretar a través de una clase de vista"
  - "vistas, interfaz y entrada de usuario"
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 5
---
# Interpretar la entrada del usuario a trav&#233;s de una vista
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Otras funciones miembro desde la vista controlan e interpretan todos los datos proporcionados por el usuario.  Definirá normalmente funciones miembro de controladores de mensajes en la clase de vista para procesar:  
  
-   Windows [mensajes](../mfc/messages.md) generado por acciones del teclado y de mouse.  
  
-   [Comandos](../mfc/user-interface-objects-and-command-ids.md) de menús, botones de la barra de herramientas, y las teclas de aceleración.  
  
 Estas funciones miembro de controladores de mensajes interpretan las siguientes acciones como entrada de datos, la selección, o editar, como mover datos a y desde el portapapeles:  
  
-   Los movimientos del mouse y haga clic en, arrastres, y hace doble clic en  
  
-   Pulsaciones de tecla  
  
-   Comandos de menú  
  
 Los mensajes de Windows vista controla depende de la aplicación necesita.  
  
 [Temas del control de mensajes y de asignación](../mfc/message-handling-and-mapping.md) explica cómo asignar los elementos de menú y otros objetos de la interfaz de usuario a los comandos y cómo enlazar los comandos el controlador funcionan.  [Temas del control de mensajes y de asignación](../mfc/message-handling-and-mapping.md) también explica cómo MFC enruta comandos y envía los mensajes estándar de Windows a los objetos que contienen los controladores para ellos.  
  
 Por ejemplo, la aplicación puede necesitar implementar el gráfico directo del mouse en la vista.  El ejemplo scribble muestra cómo controlar `WM_LBUTTONDOWN`, `WM_MOUSEMOVE`, y los mensajes de `WM_LBUTTONUP` respectivamente para iniciar, para continuar, y cerrar el gráfico de un segmento de línea.  Por otra parte, puede ser necesario a veces interpretar un clic del mouse en la vista como selección.  La función de controlador de `OnLButtonDown` de vista determinaría si el usuario drenaba o seleccionaba.  Si seleccionó, el controlador determinaría si el clic estaba dentro de los límites de un objeto en la vista y, si es así modifica la pantalla para mostrar el objeto como seleccionado.  
  
 La vista también podría controlar ciertos comandos de menú, como los del menú de edición al usuario, a la copia, a pegar, o los datos seleccionados cancelación mediante el portapapeles.  Estos controladores llamaría a algunas de las funciones Portapapeles\- relacionadas del miembro de la clase `CWnd` para transferir un elemento de datos seleccionado a o desde el portapapeles.  
  
## Vea también  
 [Usar vistas](../mfc/using-views.md)