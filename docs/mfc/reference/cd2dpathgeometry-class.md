---
title: "CD2DPathGeometry (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DPathGeometry"
  - "CD2DPathGeometry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DPathGeometry (clase)"
ms.assetid: 686216eb-5080-4242-ace5-8fa1ce96307c
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DPathGeometry (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1PathGeometry.  
  
## Sintaxis  
  
```  
class CD2DPathGeometry : public CD2DGeometry;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DPathGeometry::CD2DPathGeometry](../Topic/CD2DPathGeometry::CD2DPathGeometry.md)|Construye un objeto CD2DPathGeometry.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DPathGeometry::Attach](../Topic/CD2DPathGeometry::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DPathGeometry::Create](../Topic/CD2DPathGeometry::Create.md)|Crea un CD2DPathGeometry.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DPathGeometry::Destroy](../Topic/CD2DPathGeometry::Destroy.md)|Destruye un objeto CD2DPathGeometry.  \(Invalida [CD2DGeometry::Destroy](../Topic/CD2DGeometry::Destroy.md).\)|  
|[CD2DPathGeometry::Detach](../Topic/CD2DPathGeometry::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DPathGeometry::GetFigureCount](../Topic/CD2DPathGeometry::GetFigureCount.md)|Recupera el número de figuras de la geometría de la ruta de acceso.|  
|[CD2DPathGeometry::GetSegmentCount](../Topic/CD2DPathGeometry::GetSegmentCount.md)|Recupera el número de segmentos de la geometría de la ruta de acceso.|  
|[CD2DPathGeometry::Open](../Topic/CD2DPathGeometry::Open.md)|Recupera el receptor de la geometría que se utiliza para rellenar la geometría de la ruta de acceso con figuras y segmentos.|  
|[CD2DPathGeometry::Stream](../Topic/CD2DPathGeometry::Stream.md)|Copia el contenido de la geometría de la ruta de acceso en el ID2D1GeometrySink especificado.|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DPathGeometry::m\_pPathGeometry](../Topic/CD2DPathGeometry::m_pPathGeometry.md)|Puntero a ID2D1PathGeometry.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
 [CD2DPathGeometry](../../mfc/reference/cd2dpathgeometry-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)