---
title: "CD2DBitmapBrush (Clase) | Microsoft Docs"
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
  - "CD2DBitmapBrush"
  - "afxrendertarget/CD2DBitmapBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DBitmapBrush (clase)"
ms.assetid: 46ebbe34-66e0-44c8-af1d-d129e851de5e
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DBitmapBrush (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1BitmapBrush.  
  
## Sintaxis  
  
```  
class CD2DBitmapBrush : public CD2DBrush;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::CD2DBitmapBrush](../Topic/CD2DBitmapBrush::CD2DBitmapBrush.md)|Sobrecargado.  Construye un objeto CD2DBitmapBrush desde el archivo.|  
|[CD2DBitmapBrush::~CD2DBitmapBrush](../Topic/CD2DBitmapBrush::~CD2DBitmapBrush.md)|El destructor.  Se llama cuando se destruye un objeto Brush de mapa de bits D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::Attach](../Topic/CD2DBitmapBrush::Attach.md)|Adjunta la interfaz de recurso existente al objeto|  
|[CD2DBitmapBrush::Create](../Topic/CD2DBitmapBrush::Create.md)|Crea un CD2DBitmapBrush.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DBitmapBrush::Destroy](../Topic/CD2DBitmapBrush::Destroy.md)|Destruye un objeto CD2DBitmapBrush.  \(Invalida [CD2DBrush::Destroy](../Topic/CD2DBrush::Destroy.md).\)|  
|[CD2DBitmapBrush::Detach](../Topic/CD2DBitmapBrush::Detach.md)|Desasocia la interfaz de recurso del objeto|  
|[CD2DBitmapBrush::Get](../Topic/CD2DBitmapBrush::Get.md)|Devuelve la interfaz ID2D1BitmapBrush|  
|[CD2DBitmapBrush::GetBitmap](../Topic/CD2DBitmapBrush::GetBitmap.md)|Obtiene el origen del mapa de bits que este pincel utiliza para pintar|  
|[CD2DBitmapBrush::GetExtendModeX](../Topic/CD2DBitmapBrush::GetExtendModeX.md)|Obtiene el método por el que el pincel coloca en mosaico horizontalmente aquellas áreas que se extienden más allá de su mapa de bits|  
|[CD2DBitmapBrush::GetExtendModeY](../Topic/CD2DBitmapBrush::GetExtendModeY.md)|Obtiene el método por el que el pincel coloca en mosaico verticalmente aquellas áreas que se extienden más allá de su mapa de bits|  
|[CD2DBitmapBrush::GetInterpolationMode](../Topic/CD2DBitmapBrush::GetInterpolationMode.md)|Obtiene el método de interpolación utilizado cuando el mapa de bits del pincel se escala o gira|  
|[CD2DBitmapBrush::SetBitmap](../Topic/CD2DBitmapBrush::SetBitmap.md)|Especifica el origen del mapa de bits que este pincel utiliza para pintar|  
|[CD2DBitmapBrush::SetExtendModeX](../Topic/CD2DBitmapBrush::SetExtendModeX.md)|Especifica cómo el pincel coloca en mosaico horizontalmente aquellas áreas que se extienden más allá de su mapa de bits|  
|[CD2DBitmapBrush::SetExtendModeY](../Topic/CD2DBitmapBrush::SetExtendModeY.md)|Especifica cómo el pincel coloca en mosaico verticalmente aquellas áreas que se extienden más allá de su mapa de bits|  
|[CD2DBitmapBrush::SetInterpolationMode](../Topic/CD2DBitmapBrush::SetInterpolationMode.md)|Especifica el modo de interpolación que se utiliza cuando el mapa de bits del pincel se escala o gira|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::CommonInit](../Topic/CD2DBitmapBrush::CommonInit.md)|Inicializa el objeto|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::operator ID2D1BitmapBrush\*](../Topic/CD2DBitmapBrush::operator%20ID2D1BitmapBrush*.md)|Devuelve la interfaz ID2D1BitmapBrush|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DBitmapBrush::m\_pBitmap](../Topic/CD2DBitmapBrush::m_pBitmap.md)|Almacena un puntero a un objeto CD2DBitmap.|  
|[CD2DBitmapBrush::m\_pBitmapBrush](../Topic/CD2DBitmapBrush::m_pBitmapBrush.md)|Almacena un puntero a un objeto ID2D1BitmapBrush.|  
|[CD2DBitmapBrush::m\_pBitmapBrushProperties](../Topic/CD2DBitmapBrush::m_pBitmapBrushProperties.md)|Propiedades de pincel de mapa de bits.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DBrush](../../mfc/reference/cd2dbrush-class.md)  
  
 [CD2DBitmapBrush](../../mfc/reference/cd2dbitmapbrush-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)