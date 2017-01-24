---
title: "CSize Class | Microsoft Docs"
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
  - "CSize"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CSize class"
  - "dimensiones"
  - "dimensiones, MFC"
  - "SIZE"
ms.assetid: fb2cf85a-0bc1-46f8-892b-309c108b52ae
caps.latest.revision: 20
caps.handback.revision: 10
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CSize Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

similar a la estructura de Windows [CALIBRE](http://msdn.microsoft.com/library/windows/desktop/dd145106) , que implementa una coordenada relativa o una posición.  
  
## Sintaxis  
  
```  
class CSize : public tagSIZE  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSize::CSize](../Topic/CSize::CSize.md)|Crea un objeto `CSize`.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CSize::operator \-](../Topic/CSize::operator%20-.md)|Resta dos tamaños.|  
|[CSize::operator \!\=](../Topic/CSize::operator%20!=.md)|Comprueba la desigualdad entre `CSize` y un tamaño.|  
|[CSize::operator \+](../Topic/CSize::operator%20+.md)|Agrega dos tamaños.|  
|[CSize::operator \+\=](../Topic/CSize::operator%20+=.md)|Agrega un tamaño a `CSize`.|  
|[CSize::operator \-\=](../Topic/CSize::operator%20-=.md)|Resta un tamaño de `CSize`.|  
|[CSize::operator \=\=](../Topic/CSize::operator%20==.md)|Comprueba la igualdad entre `CSize` y un tamaño.|  
  
## Comentarios  
 Esta clase se deriva de la estructura de **CALIBRE** .  Esto significa que puede pasar `CSize` en un parámetro que pide **CALIBRE** y que sean miembros de datos los miembros de datos de la estructura de **CALIBRE** accesibles de `CSize`.  
  
 los miembros de **CX** y de **CY** de **CALIBRE** \(y de `CSize`\) son públicos.  Además, `CSize` implementa funciones miembro para manipular la estructura de **CALIBRE** .  
  
> [!NOTE]
>  Para obtener más información sobre clases de utilidad compartidas \(como `CSize`\), vea [clases compartidas](../../atl-mfc-shared/atl-mfc-shared-classes.md).  
  
## Jerarquía de herencia  
 `tagSIZE`  
  
 `CSize`  
  
## Requisitos  
 **encabezado:** atltypes.h  
  
## Vea también  
 [ejemplo MDI de MFC](../../top/visual-cpp-samples.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CRect Class](../../atl-mfc-shared/reference/crect-class.md)   
 [CPoint Class](../../atl-mfc-shared/reference/cpoint-class.md)