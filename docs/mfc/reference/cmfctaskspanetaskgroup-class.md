---
title: "CMFCTasksPaneTaskGroup Class | Microsoft Docs"
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
  - "CMFCTasksPaneTaskGroup"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCTasksPaneTaskGroup class"
ms.assetid: 2111640b-a46e-4b27-b033-29e88632b86a
caps.latest.revision: 33
caps.handback.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CMFCTasksPaneTaskGroup Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La clase de `CMFCTasksPaneTaskGroup` es una clase auxiliar utilizada por el control de [CMFCTasksPane](../../mfc/reference/cmfctaskspane-class.md) .  Los objetos de `CMFCTasksPaneTaskGroup` tipo representan *un grupo de tareas*.  El grupo de tareas es una lista de elementos que el marco presente en un cuadro independiente que tiene un botón de contraer.  El cuadro puede tener una leyenda opcional \(nombre de grupo\).  Si un grupo está contraído, la lista de tareas no está visible.  
  
## Sintaxis  
  
```  
class CMFCTasksPaneTaskGroup : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup](../Topic/CMFCTasksPaneTaskGroup::CMFCTasksPaneTaskGroup.md)|Crea un objeto `CMFCTasksPaneTaskGroup`.|  
|`CMFCTasksPaneTaskGroup::~CMFCTasksPaneTaskGroup`|Un destructor.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::SetACCData](../Topic/CMFCTasksPaneTaskGroup::SetACCData.md)|Determina los datos de accesibilidad para el grupo de tareas actual.|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCTasksPaneTaskGroup::m\_bIsBottom](../Topic/CMFCTasksPaneTaskGroup::m_bIsBottom.md)|Determina si el grupo de tareas está alineado al control del panel de tareas.|  
|[CMFCTasksPaneTaskGroup::m\_bIsCollapsed](../Topic/CMFCTasksPaneTaskGroup::m_bIsCollapsed.md)|determina si el grupo de tareas está contraído.|  
|[CMFCTasksPaneTaskGroup::m\_bIsSpecial](../Topic/CMFCTasksPaneTaskGroup::m_bIsSpecial.md)|Determina si el grupo de tareas es *especial.* El marco muestra leyendas especiales en un color diferente.|  
|[CMFCTasksPaneTaskGroup::m\_lstTasks](../Topic/CMFCTasksPaneTaskGroup::m_lstTasks.md)|Contiene la lista de tareas.|  
|[CMFCTasksPaneTaskGroup::m\_rect](../Topic/CMFCTasksPaneTaskGroup::m_rect.md)|Especifica el rectángulo delimitador de la leyenda del grupo.|  
|[CMFCTasksPaneTaskGroup::m\_rectGroup](../Topic/CMFCTasksPaneTaskGroup::m_rectGroup.md)|Especifica el rectángulo delimitador del grupo.|  
|[CMFCTasksPaneTaskGroup::m\_strName](../Topic/CMFCTasksPaneTaskGroup::m_strName.md)|Especifica el nombre del grupo.|  
  
## Comentarios  
 La ilustración siguiente se muestra un grupo de tareas expandido:  
  
 ![Grupo de tareas, expandido](../../mfc/reference/media/nexttaskgrpexpand.png "NextTaskGrpExpand")  
  
 La ilustración siguiente se muestra un grupo de tareas contraído:  
  
 ![Grupo de tareas contraído](../../mfc/reference/media/nexttaskgrpcollapse.png "NextTaskGrpCollapse")  
  
 La ilustración siguiente muestra un grupo de tareas sin una leyenda:  
  
 ![Grupo de tareas sin título](../../mfc/reference/media/nexttaskgrpnocapt.png "NextTaskGrpNoCapt")  
  
 La ilustración siguiente muestra dos grupos de tareas.  Estableciendo marca al primer grupo de tareas como especial `m_bIsSpecial` marca a `TRUE`, mientras que el segundo grupo de tareas no es especial.  Observe que la leyenda para el primer grupo de tareas es más oscura que el segundo grupo de tareas:  
  
 ![Grupo de tareas especial](../../mfc/reference/media/nexttaskgrpspecial.png "NextTaskGrpSpecial")  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CMFCTasksPaneTaskGroup](../../mfc/reference/cmfctaskspanetaskgroup-class.md)  
  
## Requisitos  
 **encabezado:** afxTasksPane.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCTasksPane Class](../../mfc/reference/cmfctaskspane-class.md)   
 [CMFCTasksPaneTask Class](../../mfc/reference/cmfctaskspanetask-class.md)   
 [CMFCOutlookBar \(Clase\)](../../mfc/reference/cmfcoutlookbar-class.md)   
 [CObject Class](../../mfc/reference/cobject-class.md)