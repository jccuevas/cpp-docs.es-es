---
title: "Estilos de barra de desplazamiento | Microsoft Docs"
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
  - "SBS_VERT"
  - "SBS_SIZEBOXBOTTOMRIGHTALIGN"
  - "SBS_LEFTALIGN"
  - "SBS_RIGHTALIGN"
  - "SBS_TOPALIGN"
  - "SBS_SIZEBOXTOPLEFTALIGN"
  - "SBS_BOTTOMALIGN"
  - "SBS_SIZEBOX"
  - "SBS_HORZ"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "SBS_BOTTOMALIGN (constante)"
  - "SBS_HORZ (constante)"
  - "SBS_LEFTALIGN (constante)"
  - "SBS_RIGHTALIGN (constante)"
  - "SBS_SIZEBOX (constante)"
  - "SBS_SIZEBOXBOTTOMRIGHTALIGN (constante)"
  - "SBS_SIZEBOXTOPLEFTALIGN (constante)"
  - "SBS_TOPALIGN (constante)"
  - "SBS_VERT (constante)"
  - "barras de desplazamiento, estilos"
ms.assetid: 8bcde35b-387d-49ae-bdd6-7cda9f5dae26
caps.latest.revision: 12
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estilos de barra de desplazamiento
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

-   **SBS\_BOTTOMALIGN** utilizado con el estilo de **SBS\_HORZ** .  El borde inferior de la barra de desplazamiento se alinee con el borde inferior del rectángulo especificado en la función miembro de **crear** .  La barra de desplazamiento tiene el alto predeterminado para las barras de desplazamiento del sistema.  
  
-   **SBS\_HORZ** Designates a la barra de desplazamiento horizontal.  Si no se especifica el estilo de **SBS\_BOTTOMALIGN** ni de **SBS\_TOPALIGN** , la barra de desplazamiento tiene el alto, el ancho, y la posición especificada en la función miembro de **crear** .  
  
-   **SBS\_LEFTALIGN** utilizado con el estilo de **SBS\_VERT** .  El borde izquierdo de la barra de desplazamiento se alinee con el borde izquierdo del rectángulo especificado en la función miembro de **crear** .  La barra de desplazamiento tiene el ancho predeterminado para las barras de desplazamiento del sistema.  
  
-   **SBS\_RIGHTALIGN** utilizado con el estilo de **SBS\_VERT** .  El borde derecho de la barra de desplazamiento se alinee con el borde derecho del rectángulo especificado en la función miembro de **crear** .  La barra de desplazamiento tiene el ancho predeterminado para las barras de desplazamiento del sistema.  
  
-   **SBS\_SIZEBOX** Designates un control de tamaño.  Si no se especifica el estilo de **SBS\_SIZEBOXBOTTOMRIGHTALIGN** ni de **SBS\_SIZEBOXTOPLEFTALIGN** , el control de tamaño tiene el alto, el ancho, y la posición especificada en la función miembro de **crear** .  
  
-   **SBS\_SIZEBOXBOTTOMRIGHTALIGN** utilizado con el estilo de **SBS\_SIZEBOX** .  La esquina inferior derecha del control de tamaño se alinea con la esquina inferior derecha del rectángulo especificado en la función miembro de **crear** .  El control de tamaño tiene el tamaño predeterminado de los controles de tamaño del sistema.  
  
-   **SBS\_SIZEBOXTOPLEFTALIGN** utilizado con el estilo de **SBS\_SIZEBOX** .  La esquina superior izquierda del control de tamaño se alinea con la esquina superior izquierda del rectángulo especificado en la función miembro de **crear** .  El control de tamaño tiene el tamaño predeterminado de los controles de tamaño del sistema.  
  
-   **SBS\_SIZEGRIP** Same que **SBS\_SIZEBOX**, pero con un borde elevado.  
  
-   **SBS\_TOPALIGN** utilizado con el estilo de **SBS\_HORZ** .  El borde superior de la barra de desplazamiento se alinea al borde superior del rectángulo especificado en la función miembro de **crear** .  La barra de desplazamiento tiene el alto predeterminado para las barras de desplazamiento del sistema.  
  
-   **SBS\_VERT** Designates a la barra de desplazamiento vertical.  Si no se especifica el estilo de **SBS\_RIGHTALIGN** ni de **SBS\_LEFTALIGN** , la barra de desplazamiento tiene el alto, el ancho, y la posición especificada en la función miembro de **crear** .  
  
## Vea también  
 [Estilos utilizados por MFC](../../mfc/reference/styles-used-by-mfc.md)   
 [CScrollBar::Create](../Topic/CScrollBar::Create.md)   
 [Scroll Bar Control Styles](http://msdn.microsoft.com/library/windows/desktop/bb787533)