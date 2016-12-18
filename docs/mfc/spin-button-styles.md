---
title: "Estilos de bot&#243;n de cuadro de n&#250;mero | Microsoft Docs"
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
  - "CSpinButtonCtrl (clase), estilos"
  - "control de botón de número, estilos"
  - "estilos, CSpinButtonCtrl"
  - "estilos, control de botón de número"
ms.assetid: fb4a7f6f-9182-47be-bccf-0728fdc5332f
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estilos de bot&#243;n de cuadro de n&#250;mero
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Muchos de los valores de un botón de número \([CSpinButtonCtrl](../mfc/reference/cspinbuttonctrl-class.md)\) se controlan mediante estilos.  Puede establecer los estilos siguientes en la ventana de **Propiedades** en el editor de cuadros de diálogo.  
  
-   **Orientación** Either Vertical u Horizontal.  Controla la guía de los botones de flecha.  Asociado al estilo de `UDS_HORZ` .  
  
-   **Alineación** Uno de independiente, Left, o derecho.  Controla la ubicación del botón de número.  Posición izquierda y derecha del botón vuelta al lado de la ventana de relacionada.  El ancho de la ventana de relacionada se reduce para incluir el botón de número.  Asociado a los estilos de `UDS_ALIGNLEFT` y de `UDS_ALIGNRIGHT` .  
  
-   **Auto Buddy** seleccionará automáticamente la ventana anterior en orden Z como ventana de relacionada al botón de número.  En una plantilla de cuadro de diálogo, éste es el control que precede al botón de número en el orden de tabulación.  Asociado al estilo de `UDS_AUTOBUDDY` .  
  
-   **Set Buddy Integer** hace que el control de número para incrementar y disminuya la leyenda de la ventana de relacionada con los cambios de la posición actual.  Asociado al estilo de `UDS_SETBUDDYINT` .  
  
-   Inserción de**No Thousands**No no el separador de miles en el valor de la leyenda de la ventana de relacionada.  Asociado al estilo de `UDS_NOTHOUSANDS` .  
  
    > [!NOTE]
    >  Establezca este estilo si desea utilizar el diálogo intercambio de datos \(DDX\) para obtener el valor entero del control de relacionada.  `DDX_Text` no acepta los separadores de miles incrustados.  
  
-   **Ajustar** Hace que la posición de “ajuste” como valor se aumenta o se reduzca más allá del intervalo del control.  Asociado al estilo de `UDS_WRAP` .  
  
-   **Arrow Keys** hace que el botón de número para aumentar o disminuir la posición cuando se presione la FLECHA ARRIBA y las teclas de flecha abajo.  Asociado al estilo de `UDS_ARROWKEYS` .  
  
## Vea también  
 [Usar CSpinButtonCtrl](../mfc/using-cspinbuttonctrl.md)   
 [Controles](../mfc/controls-mfc.md)