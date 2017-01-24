---
title: "Procesar mensajes de notificaci&#243;n en los controles de cuadro combinado extendido | Microsoft Docs"
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
  - "cuadros combinados extendidos, notificaciones"
  - "notificaciones, controles de cuadro combinado extendido"
ms.assetid: 4e442758-d054-4746-bb1a-6ff84accb127
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Procesar mensajes de notificaci&#243;n en los controles de cuadro combinado extendido
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

A medida que los usuarios interactúan con el cuadro combinado extendido, el control \(`CComboBoxEx`\) envía mensajes de notificación a su ventana primaria, normalmente un objeto de vista o cuadro de diálogo. Controle estos mensajes si desea hacer algo en respuesta. Por ejemplo, cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control, se envía la notificación **CBEN\_BEGINEDIT**.  
  
 Use la ventana Propiedades para agregar controladores de notificación a la clase primaria para aquellos mensajes que desee implementar.  
  
 En la lista siguiente se describen las distintas notificaciones que envía el control de cuadro combinado extendido.  
  
-   **CBEN\_BEGINEDIT** Se envía cuando el usuario activa la lista desplegable o hace clic en el cuadro de edición del control.  
  
-   **CBEN\_DELETEITEM** Se envía cuando se elimina un elemento.  
  
-   **CBEN\_DRAGBEGIN** Se envía cuando el usuario comienza a arrastrar la imagen del elemento que se muestra en la parte de edición del control.  
  
-   **CBEN\_ENDEDIT** Se envía cuando el usuario finaliza una operación en el cuadro de edición o selecciona un elemento de la lista desplegable del control.  
  
-   **CBEN\_GETDISPINFO** Se envía para recuperar información de visualización sobre un elemento de devolución de llamada.  
  
-   **CBEN\_INSERTITEM** Se envía cuando se inserta un nuevo elemento en el control.  
  
## Vea también  
 [Usar CComboBoxEx](../mfc/using-ccomboboxex.md)   
 [Controles](../mfc/controls-mfc.md)