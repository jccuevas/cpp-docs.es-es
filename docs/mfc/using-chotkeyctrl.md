---
title: "Usar CHotKeyCtrl | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "CHotKeyCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CHotKeyCtrl (clase), utilizar"
  - "controles de tecla de acceso rápido"
  - "claves, acceso rápido y CHotKeyCtrl"
ms.assetid: 9b207117-d848-4224-8888-c3d197bb0c95
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Usar CHotKeyCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control de la tecla de acceso rápido, representado por la clase [CHotKeyCtrl](../mfc/reference/chotkeyctrl-class.md), es una ventana que muestra una representación de texto de la combinación de teclas el usuario en ella, como CTRL\+MAYÚS\+Q.  También mantiene una representación interna de esta clave en forma de código de tecla virtual y conjunto de marcas que representan el estado del cambio.  El control de la tecla de acceso rápido no establece realmente la tecla de acceso rápido — hacerlo depende del programa. \(Para obtener una lista de códigos de tecla virtual estándar, vea Winuser.h.\)  
  
 Utilice un control de la tecla de acceso rápido para obtener la entrada de un usuario que tecla de acceso rápido para asociar a una ventana o un subproceso.  Los controles de la tecla de acceso rápido suelen utilizarse en los cuadros de diálogo, como se puede mostrar el pedir al usuario asignar una tecla de acceso rápido.  Es responsabilidad del programa recuperar valores que describen la tecla de acceso rápido de controles de la tecla de acceso rápido y llamar a funciones adecuadas para asociar la tecla de acceso rápido a una ventana o un subproceso.  
  
## ¿Sobre qué desea obtener más información?  
  
-   [Utilizar un Control de la tecla de acceso rápido](../mfc/using-a-hot-key-control.md)  
  
-   [Establecer una tecla de acceso rápido](../mfc/setting-a-hot-key.md)  
  
-   [Teclas de acceso rápido globales](../mfc/global-hot-keys.md)  
  
-   [Teclas de acceso rápido Subproceso\-específicas](../mfc/thread-specific-hot-keys.md)  
  
## Vea también  
 [Controles](../mfc/controls-mfc.md)