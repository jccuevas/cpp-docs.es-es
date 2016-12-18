---
title: "CMFCTasksPaneTask Class | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCTasksPaneTask"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTasksPaneTask class"
ms.assetid: c5a7513b-cd8f-4e2e-b16f-650e1fe30954
caps.latest.revision: 27
caps.handback.revision: 15
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCTasksPaneTask Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCTasksPaneTask` es una clase auxiliar que representa las tareas para el control del panel de tareas \([CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md)\).  el objeto de tarea representa un elemento en el grupo de tareas \([CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)\).  Cada tarea puede tener un comando que el marco se ejecuta cuando un usuario hace clic en la tarea y el icono que aparece a la izquierda del nombre de tarea.  
  
## Sintaxis  
  
```  
class CMFCTasksPaneTask : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTask::CMFCTasksPaneTask](../Topic/CMFCTasksPaneTask::CMFCTasksPaneTask.md)|Crea e inicializa un objeto `CMFCTasksPaneTask`.|  
|`CMFCTasksPaneTask::~CMFCTasksPaneTask`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTask::SetACCData](../Topic/CMFCTasksPaneTask::SetACCData.md)|Determina los datos de accesibilidad para la tarea actual.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTask::m\_bAutoDestroyWindow](../Topic/CMFCTasksPaneTask::m_bAutoDestroyWindow.md)|Determina si la ventana de la tarea automáticamente se destruida.|  
|[CMFCTasksPaneTask::m\_bIsBold](../Topic/CMFCTasksPaneTask::m_bIsBold.md)|Determina si el marco dibuja una etiqueta de la tarea en negrita.|  
|[CMFCTasksPaneTask::m\_dwUserData](../Topic/CMFCTasksPaneTask::m_dwUserData.md)|Contiene los datos definidos por el usuario que el marco asociado a la tarea.  Establece en cero si la tarea no tiene datos asociados.|  
|[CMFCTasksPaneTask::m\_hwndTask](../Topic/CMFCTasksPaneTask::m_hwndTask.md)|Un identificador de la ventana de la tarea.|  
|[CMFCTasksPaneTask::m\_nIcon](../Topic/CMFCTasksPaneTask::m_nIcon.md)|El índice en la lista de imágenes de la imagen que el marco muestra junto a la tarea.|  
|[CMFCTasksPaneTask::m\_nWindowHeight](../Topic/CMFCTasksPaneTask::m_nWindowHeight.md)|el alto de la ventana de la tarea.  Si la tarea no tiene ninguna ventana de tarea, este valor es cero.|  
|[CMFCTasksPaneTask::m\_pGroup](../Topic/CMFCTasksPaneTask::m_pGroup.md)|Un puntero a `CMFCTasksPaneTaskGroup` que esta tarea pertenece.|  
|[CMFCTasksPaneTask::m\_rect](../Topic/CMFCTasksPaneTask::m_rect.md)|especifica el rectángulo delimitador de la tarea.|  
|[CMFCTasksPaneTask::m\_strName](../Topic/CMFCTasksPaneTask::m_strName.md)|Nombre de la tarea.|  
|[CMFCTasksPaneTask::m\_uiCommandID](../Topic/CMFCTasksPaneTask::m_uiCommandID.md)|Especifica el identificador del comando que el marco se ejecuta cuando el usuario hace clic en la tarea.  Si este valor no es un identificador válido del comando, la tarea se trata como etiqueta simple.|  
  
## Comentarios  
 La ilustración siguiente se muestra un grupo de tareas que contiene tres tareas:  
  
 ![Grupo de tareas, expandido](../../mfc/reference/media/nexttaskgrpexpand.png "NextTaskGrpExpand")  
  
> [!NOTE]
>  Si una tarea no tiene un identificador válido del comando, se trata como una etiqueta simple.  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTask](../../mfc/reference/cmfctaskspanetask-class.md)  
  
## Requisitos  
 **encabezado:** afxTasksPane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)