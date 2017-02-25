---
title: "Rutinas de intercambio de datos de cuadros de di&#225;logo est&#225;ndar | Microsoft Docs"
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
  - "cuadro de diálogo estándar, rutinas de intercambio de datos"
ms.assetid: c6adb7f3-f9af-4cc5-a9ea-315c5b60ad1a
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 14
---
# Rutinas de intercambio de datos de cuadros de di&#225;logo est&#225;ndar
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Este tema muestra las rutinas de intercambio de datos de diálogo estándar \(DDX\) utilizadas para controles comunes de cuadros de diálogo MFC.  
  
> [!NOTE]
>  Las rutinas de intercambio de datos de diálogo estándar se definen en el archivo de encabezado afxdd\_.h.  Sin embargo, las aplicaciones deben incluir afxwin.h.  
  
### Funciones DDX  
  
|||  
|-|-|  
|[DDX\_CBIndex](../Topic/DDX_CBIndex.md)|Inicializa o recupera el índice de la selección actual de un control de cuadro combinado.|  
|[DDX\_CBString](../Topic/DDX_CBString.md)|Inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|  
|[DDX\_CBStringExact](../Topic/DDX_CBStringExact.md)|Inicializa o recupera el contenido actual del campo de edición de un control de cuadro combinado.|  
|[DDX\_Check](../Topic/DDX_Check.md)|Inicializa o recupera el estado actual de un control checkbox.|  
|[DDX\_Control](../Topic/DDX_Control.md)|Crea una subclase un control determinado dentro de un cuadro de diálogo.|  
|[DDX\_DateTimeCtrl](../Topic/DDX_DateTimeCtrl.md)|Inicializa o recupera datos de fecha o de hora de un control de selector de fecha y hora.|  
|[DDX\_IPAddress](../Topic/DDX_IPAddress.md)|Inicializa o recupera el valor actual de una dirección IP.|  
|[DDX\_LBIndex](../Topic/DDX_LBIndex.md)|Inicializa o recupera el índice de la selección actual de un control de cuadro de lista.|  
|[DDX\_LBString](../Topic/DDX_LBString.md)|Inicializa o recupera la selección actual en un control de cuadro de lista.|  
|[DDX\_LBStringExact](../Topic/DDX_LBStringExact.md)|Inicializa o recupera la selección actual en un control de cuadro de lista.|  
|[DDX\_MonthCalCtrl](../Topic/DDX_MonthCalCtrl.md)|Inicializa o recupera el valor actual de un control de calendario mensual.|  
|[DDX\_Radio](../Topic/DDX_Radio.md)|Inicializa o recupera los 0 índices basados en el control de radio que se comprueba actualmente dentro de un grupo de controles de radio.|  
|[DDX\_Scroll](../Topic/DDX_Scroll.md)|Inicializa o recupera la posición actual del control de un control de desplazamiento.|  
|[DDX\_Slider](../Topic/DDX_Slider.md)|Inicializa o recupera la posición actual del control de un control deslizante.|  
|[DDX\_Text](../Topic/DDX_Text.md)|Inicializa o recupera el valor actual de un control de edición.|  
  
## Vea también  
 [Rutinas estándar de validación de datos de cuadro de diálogo](../../mfc/reference/standard-dialog-data-validation-routines.md)   
 [Macros y variables globales](../../mfc/reference/mfc-macros-and-globals.md)