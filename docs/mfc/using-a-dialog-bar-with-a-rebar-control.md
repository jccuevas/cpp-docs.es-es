---
title: "Usar una barra de cuadro de di&#225;logo con un control Rebar | Microsoft Docs"
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
  - "WM_EX_TRANSPARENT"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "barras de cuadro de diálogo, utilizar con bandas rebar"
  - "controles rebar, barras de cuadro de diálogo"
  - "WS_EX_TRANSPARENT (estilo)"
ms.assetid: e528cea0-6b81-4bdf-9643-7c03b6176590
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar una barra de cuadro de di&#225;logo con un control Rebar
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Como se indica en [Controles y Bandas Rebar](../mfc/rebar-controls-and-bands.md), cada banda sólo puede contener una ventana secundaria \(o el control\).  Esto podría ser una limitación si desea tener más de una ventana secundaria por banda.  Una solución conveniente es crear un recurso de la barra de cuadro diálogo con varios controles y agregar una banda rebar \(que contiene la barra de cuadro diálogo\) al control rebar.  
  
 Normalmente, si desea banda de la barra de cuadro diálogo aparezca transparente, establecería **WS\_EX\_TRANSPARENT** extendidas estilo para el objeto de la barra de cuadro de diálogo.  Sin embargo, como **WS\_EX\_TRANSPARENT** tiene algunos problemas correctamente el dibujo del fondo de una barra de cuadro de diálogo, necesitará hacer el trabajo algún adicional para lograr el efecto deseado.  
  
 El procedimiento siguiente detalla los pasos necesarios para lograr la transparencia sin utilizar **WS\_EX\_TRANSPARENT** extendidas estilo.  
  
### Para implementar una barra de cuadro diálogo transparente en una banda rebar  
  
1.  Mediante [Agregue el cuadro de diálogo de la clase](../mfc/reference/adding-an-mfc-class.md), agregue una nueva clase \(por ejemplo, `CMyDlgBar`\) que implementa el objeto de la barra de cuadro de diálogo.  
  
2.  Agregue un controlador para el mensaje de `WM_ERASEBKGND` .  
  
3.  En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#29](../mfc/codesnippet/CPP/using-a-dialog-bar-with-a-rebar-control_1.cpp)]  
  
4.  Agregue un controlador para el mensaje de `WM_MOVE` .  
  
5.  En el nuevo controlador, modifique el código existente para que coincida con el ejemplo siguiente:  
  
     [!code-cpp[NVC_MFCControlLadenDialog#30](../mfc/codesnippet/CPP/using-a-dialog-bar-with-a-rebar-control_2.cpp)]  
  
 Los nuevos controladores simulan la transparencia de la barra de cuadro diálogo reenviando el mensaje de `WM_ERASEBKGND` a la ventana primaria y fuerza una repintura cada vez que se mueve el objeto de la barra de cuadro de diálogo.  
  
## Vea también  
 [Usar CReBarCtrl](../mfc/using-crebarctrl.md)   
 [Controles](../mfc/controls-mfc.md)