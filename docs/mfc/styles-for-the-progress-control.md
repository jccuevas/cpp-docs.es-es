---
title: "Estilos para el control de progreso | Microsoft Docs"
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
  - "CProgressCtrl (clase), estilos"
  - "PBS_SMOOTH (estilo)"
  - "PBS_VERTICAL (estilo)"
  - "controles de progreso [C++], estilos"
ms.assetid: 39eb8081-bc20-4552-91b9-e7cdd1b7d8ae
caps.latest.revision: 9
caps.handback.revision: 5
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estilos para el control de progreso
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando crea inicialmente el control de progreso \([CProgressCtrl::Create](../Topic/CProgressCtrl::Create.md)\), utilice el parámetro de `dwStyle` para especificar los estilos de ventana deseadas para el control de progreso.  Los detalles de la lista los estilos de ventana aplicables.  El control omite cualquier estilo de ventana con excepción de las que se mostrarán aquí.  Debe crear siempre el control como una ventana secundaria, normalmente desde un elemento primario del cuadro de diálogo.  
  
|Estilo de ventana|Efecto|  
|-----------------------|------------|  
|`WS_BORDER`|Crea un borde alrededor de la ventana.|  
|**WS\_CHILD**|Crea una ventana secundaria \(debe utilizar siempre para `CProgressCtrl`\).|  
|**WS\_CLIPCHILDREN**|Excluye el área ocupada por las ventanas secundarias cuando se dibuja dentro de la ventana primaria.  Se utiliza al crear la ventana primaria.|  
|**WS\_CLIPSIBLINGS**|Recorta las ventanas secundarias en relación con.|  
|**WS\_DISABLED**|Crea una ventana que se deshabilite inicialmente.|  
|**WS\_VISIBLE**|Crea una ventana que se muestra inicialmente.|  
|**WS\_TABSTOP**|Especifica que el control puede recibir el foco cuando el usuario presione la tecla TAB para desplazarse a.|  
  
 Además, puede especificar dos estilos que se aplican al control, a `PBS_VERTICAL` y a `PBS_SMOOTH`progreso.  
  
 Utilice `PBS_VERTICAL` para orientar el control verticalmente, en lugar de horizontalmente.  Utilice `PBS_SMOOTH` para rellenar el control completamente, en lugar de mostrar pequeños cuadrados descritos que rellenan el control mejorado.  
  
 Sin el estilo de `PBS_SMOOTH` :  
  
 ![Estilo de barra de progreso estándar](../mfc/media/vc4ruw1.png "vc4RUW1")  
  
 Con `PBS_SMOOTH` y estilos de `PBS_VERTICAL` :  
  
 ![Estilo de barra de progreso, suave y vertical](../mfc/media/vc4ruw2.png "vc4RUW2")  
  
 Para obtener más información, vea [Estilos de ventana](../mfc/reference/frame-window-styles-mfc.md) en *la referencia de MFC*.  
  
## Vea también  
 [Usar CProgressCtrl](../mfc/using-cprogressctrl.md)