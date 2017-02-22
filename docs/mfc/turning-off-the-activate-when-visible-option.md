---
title: "Desactivar la opci&#243;n Activar cuando est&#233; visible | Microsoft Docs"
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
  - "Controles ActiveX MFC [C++], activar opciones"
  - "opción para activar cuando sea visible"
ms.assetid: 8f7ddc5a-a7a6-4da8-bcb9-1b569f0ecb48
caps.latest.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# Desactivar la opci&#243;n Activar cuando est&#233; visible
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un control tiene dos estados básicos: activo e inactivo.  Tradicionalmente, se distinguían por el hecho de que el control tuviera o no una ventana.  Un control activo tenía una ventana; un control inactivo no la tenía.  Con la introducción de la activación sin ventana, esta distinción ya no es universal, pero sigue aplicándose a muchos controles.  
  
 En comparación con el resto de inicialización habitual de un control ActiveX, la creación de una ventana es una operación muy costosa.  Idealmente, un control diferiría crear su ventana hasta absolutamente necesario.  
  
 Muchos controles no necesitan ser activo el tiempo completo que están visibles en un contenedor.  A menudo, un control puede permanecer en estado inactivo hasta que el usuario realice una operación que lo requiera volverse activo \(por ejemplo, al hacer clic con el mouse o presionando la tecla TAB\).  Para que un control para permanecer inactivo hasta el contenedor necesita activarlo, quita el marcador de **OLEMISC\_ACTIVATEWHENVISIBLE** flags diferentes del control:  
  
 [!code-cpp[NVC_MFC_AxOpt#9](../mfc/codesnippet/CPP/turning-off-the-activate-when-visible-option_1.cpp)]  
  
 El indicador de **OLEMISC\_ACTIVATEWHENVISIBLE** automáticamente se omite si desactiva la opción de **Activate When Visible** en la página de [Configuración del control](../mfc/reference/control-settings-mfc-activex-control-wizard.md) del asistente para controles ActiveX MFC cuando cree el control.  
  
## Vea también  
 [Controles ActiveX MFC: Optimización](../mfc/mfc-activex-controls-optimization.md)