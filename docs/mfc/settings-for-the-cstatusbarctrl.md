---
title: "Configuraci&#243;n de CStatusBarCtrl | Microsoft Docs"
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
  - "CStatusBarCtrl"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CStatusBarCtrl (clase), configuración"
  - "controles de la barra de estado, configuración"
ms.assetid: adeba0c3-17f3-435c-b140-a57845e9ce49
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Configuraci&#243;n de CStatusBarCtrl
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

La posición predeterminada de una ventana de estado de [CStatusBarCtrl](../mfc/reference/cstatusbarctrl-class.md) es a lo largo de la parte inferior de la ventana primaria, pero puede especificar el estilo de `CCS_TOP` para que aparece en la parte superior del área de cliente de la ventana primaria.  
  
 Puede especificar el estilo de **SBARS\_SIZEGRIP** para incluir un control de tamaño en el extremo derecho de la ventana de estado de `CStatusBarCtrl` .  Un controlador de tamaño es similar a un borde de tamaño; es un área rectangular que el usuario puede hacer clic y arrastrar para cambiar el tamaño de la ventana primaria.  
  
> [!NOTE]
>  Si combina `CCS_TOP` y estilos de **SBARS\_SIZEGRIP** , el control resultante de tamaño no es funcional aunque el sistema lo dibuja en la ventana de estado.  
  
 El procedimiento de ventana para la ventana de estado establece automáticamente el tamaño inicial y la posición de la ventana de control.  El ancho es igual que el del área de cliente de la ventana primaria.  El alto se basa en las métricas de la fuente que está actualmente seleccionado en el contexto de dispositivo de la ventana de estado y en el ancho de los bordes de la ventana.  
  
 El procedimiento de ventana incluye automáticamente al tamaño de la ventana de estado siempre que reciba un mensaje de `WM_SIZE` .  Normalmente, cuando el tamaño de la ventana primaria, el elemento primario envía un mensaje de `WM_SIZE` a la ventana de estado.  
  
 Puede establecer el alto mínimo de área de gráfico de una ventana de estado llamando a [SetMinHeight](../Topic/CStatusBarCtrl::SetMinHeight.md), especificando el alto mínimo en píxeles.  El área de gráfico no incluye los bordes de la ventana.  
  
 Recupera el ancho de los bordes de una ventana de estado llamando a [GetBorders](../Topic/CStatusBarCtrl::GetBorders.md).  Esta función miembro incluye el puntero a una matriz de tres\- elemento que recibe el ancho del borde horizontal, de borde vertical, y del borde entre los rectángulos.  
  
## Vea también  
 [Usar CStatusBarCtrl](../mfc/using-cstatusbarctrl.md)   
 [Controles](../mfc/controls-mfc.md)