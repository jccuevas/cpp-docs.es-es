---
title: "CD2DGeometry (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CD2DGeometry"
  - "afxrendertarget/CD2DGeometry"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DGeometry (clase)"
ms.assetid: 3f95054b-fdb8-4e87-87f2-9fc3df7279ec
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 18
---
# CD2DGeometry (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1Geometry.  
  
## Sintaxis  
  
```  
class CD2DGeometry : public CD2DResource;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGeometry::CD2DGeometry](../Topic/CD2DGeometry::CD2DGeometry.md)|Construye un objeto CD2DGeometry.|  
|[CD2DGeometry::~CD2DGeometry](../Topic/CD2DGeometry::~CD2DGeometry.md)|El destructor.  Se llama cuando se destruye un objeto de geometría D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGeometry::Attach](../Topic/CD2DGeometry::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DGeometry::CombineWithGeometry](../Topic/CD2DGeometry::CombineWithGeometry.md)|Combina esta geometría con la geometría especificada y almacena el resultado en ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::CompareWithGeometry](../Topic/CD2DGeometry::CompareWithGeometry.md)|Describe la intersección entre esta geometría y la geometría especificada.  La comparación se realiza mediante la tolerancia de aplanamiento especificada.|  
|[CD2DGeometry::ComputeArea](../Topic/CD2DGeometry::ComputeArea.md)|Calcula el área de la geometría después de que ha sido transformada por la matriz especificada y reducida mediante la tolerancia especificada.|  
|[CD2DGeometry::ComputeLength](../Topic/CD2DGeometry::ComputeLength.md)|Calcula la longitud de la geometría como si cada segmento se desenrollara en una línea.|  
|[CD2DGeometry::ComputePointAtLength](../Topic/CD2DGeometry::ComputePointAtLength.md)|Calcula el vector de punto y tangente a la distancia especificada a lo largo de la geometría después de que ha sido transformado por la matriz especificada y reducido mediante la tolerancia especificada.|  
|[CD2DGeometry::Destroy](../Topic/CD2DGeometry::Destroy.md)|Destruye un objeto CD2DGeometry.  \(Invalida [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md).\)|  
|[CD2DGeometry::Detach](../Topic/CD2DGeometry::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DGeometry::FillContainsPoint](../Topic/CD2DGeometry::FillContainsPoint.md)|Indica si el área que rellena la geometría contendría el punto especificado dado por la tolerancia especificada de aplanamiento.|  
|[CD2DGeometry::Get](../Topic/CD2DGeometry::Get.md)|Devuelve la interfaz ID2D1Geometry|  
|[CD2DGeometry::GetBounds](../Topic/CD2DGeometry::GetBounds.md)||  
|[CD2DGeometry::GetWidenedBounds](../Topic/CD2DGeometry::GetWidenedBounds.md)|Obtiene los límites de la geometría una vez que se ha ensanchado por el estilo y el ancho del trazo especificado y transformado por la matriz especificada.|  
|[CD2DGeometry::IsValid](../Topic/CD2DGeometry::IsValid.md)|Comprueba la validez del recurso \(invalida [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\).|  
|[CD2DGeometry::Outline](../Topic/CD2DGeometry::Outline.md)|Calcula el contorno de la geometría y escribe el resultado en ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::Simplify](../Topic/CD2DGeometry::Simplify.md)|Crea una versión simplificada de la geometría que solo contiene líneas y, opcionalmente, curvas Bézier cúbicas y escribe el resultado en ID2D1SimplifiedGeometrySink.|  
|[CD2DGeometry::StrokeContainsPoint](../Topic/CD2DGeometry::StrokeContainsPoint.md)|Determina si el trazo de la geometría contiene el punto especificado dado el grosor del trazo especificado, el estilo y la transformación.|  
|[CD2DGeometry::Tessellate](../Topic/CD2DGeometry::Tessellate.md)|Crea un conjunto de triángulos que giran en el sentido de las agujas del reloj que cubren la geometría una vez transformado utilizando la matriz especificada y reducido mediante la tolerancia especificada.|  
|[CD2DGeometry::Widen](../Topic/CD2DGeometry::Widen.md)|Amplia la geometría por el trazo especificado y escribe el resultado en ID2D1SimplifiedGeometrySink una vez ha sido transformado por la matriz especificada y reducido mediante la tolerancia especificada.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGeometry::operator ID2D1Geometry\*](../Topic/CD2DGeometry::operator%20ID2D1Geometry*.md)|Devuelve la interfaz ID2D1Geometry|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGeometry::m\_pGeometry](../Topic/CD2DGeometry::m_pGeometry.md)|Puntero a ID2D1Geometry.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DGeometry](../../mfc/reference/cd2dgeometry-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)