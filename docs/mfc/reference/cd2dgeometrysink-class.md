---
title: "CD2DGeometrySink (Clase) | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "afxrendertarget/CD2DGeometrySink"
  - "CD2DGeometrySink"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DGeometrySink (clase)"
ms.assetid: e5e07f41-0343-4ab1-9d6b-8c62ed33c04a
caps.latest.revision: 17
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 19
---
# CD2DGeometrySink (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1GeometrySink.  
  
## Sintaxis  
  
```  
class CD2DGeometrySink;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGeometrySink::CD2DGeometrySink](../Topic/CD2DGeometrySink::CD2DGeometrySink.md)|Construye un objeto CD2DGeometrySink del objeto CD2DPathGeometry.|  
|[CD2DGeometrySink::~CD2DGeometrySink](../Topic/CD2DGeometrySink::~CD2DGeometrySink.md)|El destructor.  Se llama cuando se destruye un objeto receptor de geometría D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGeometrySink::AddArc](../Topic/CD2DGeometrySink::AddArc.md)|Agrega un arco único a la geometría de la ruta de acceso|  
|[CD2DGeometrySink::AddBezier](../Topic/CD2DGeometrySink::AddBezier.md)|Crea una curva Bézier cúbica entre el punto actual y el punto final especificado.|  
|[CD2DGeometrySink::AddBeziers](../Topic/CD2DGeometrySink::AddBeziers.md)|Crea una secuencia de curvas Bézier cúbicas y las agrega al receptor de la geometría.|  
|[CD2DGeometrySink::AddLine](../Topic/CD2DGeometrySink::AddLine.md)|Crea un segmento de línea entre el punto actual y el extremo especificado, y lo agrega al receptor de geometría.|  
|[CD2DGeometrySink::AddLines](../Topic/CD2DGeometrySink::AddLines.md)|Crea una secuencia de líneas utilizando los puntos especificados y los agrega al receptor de la geometría.|  
|[CD2DGeometrySink::AddQuadraticBezier](../Topic/CD2DGeometrySink::AddQuadraticBezier.md)|Crea una curva Bézier cuadrática entre el punto actual y el punto final especificado.|  
|[CD2DGeometrySink::AddQuadraticBeziers](../Topic/CD2DGeometrySink::AddQuadraticBeziers.md)|Agrega una secuencia de segmentos de curva Bézier cuadrática como una matriz en una llamada única.|  
|[CD2DGeometrySink::BeginFigure](../Topic/CD2DGeometrySink::BeginFigure.md)|Inicia una nueva figura en el punto especificado.|  
|[CD2DGeometrySink::Close](../Topic/CD2DGeometrySink::Close.md)|Cierra el receptor de geometría|  
|[CD2DGeometrySink::EndFigure](../Topic/CD2DGeometrySink::EndFigure.md)|Finaliza la figura actual; opcionalmente, la cierra.|  
|[CD2DGeometrySink::Get](../Topic/CD2DGeometrySink::Get.md)|Devuelve la interfaz ID2D1GeometrySink|  
|[CD2DGeometrySink::IsValid](../Topic/CD2DGeometrySink::IsValid.md)|Comprueba la validez de receptor de geometría|  
|[CD2DGeometrySink::SetFillMode](../Topic/CD2DGeometrySink::SetFillMode.md)|Especifica el método que se usa para determinar qué puntos están dentro de la geometría descrita por este receptor de geometría y qué puntos están fuera.|  
|[CD2DGeometrySink::SetSegmentFlags](../Topic/CD2DGeometrySink::SetSegmentFlags.md)|Especifica el trazo y combina las opciones que se van a aplicar a los nuevos segmentos agregados al receptor de la geometría.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGeometrySink::operator ID2D1GeometrySink\*](../Topic/CD2DGeometrySink::operator%20ID2D1GeometrySink*.md)|Devuelve la interfaz ID2D1GeometrySink|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DGeometrySink::m\_pSink](../Topic/CD2DGeometrySink::m_pSink.md)|Puntero a ID2D1GeometrySink.|  
  
## Jerarquía de herencia  
 [CD2DGeometrySink](../../mfc/reference/cd2dgeometrysink-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)