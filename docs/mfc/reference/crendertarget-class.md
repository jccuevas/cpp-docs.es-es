---
title: "CRenderTarget (Clase) | Microsoft Docs"
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
  - "CRenderTarget"
  - "afxrendertarget/CRenderTarget"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRenderTarget (clase)"
ms.assetid: 30d1607d-68d3-4d14-ac36-fdbd0ef903a1
caps.latest.revision: 17
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CRenderTarget (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para ID2D1RenderTarget.  
  
## Sintaxis  
  
```  
class CRenderTarget : public CObject;  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRenderTarget::CRenderTarget](../Topic/CRenderTarget::CRenderTarget.md)|Construye un objeto CRenderTarget.|  
|[CRenderTarget::~CRenderTarget](../Topic/CRenderTarget::~CRenderTarget.md)|El destructor.  Se llama cuando se destruye un objeto de destino de representación.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRenderTarget::Attach](../Topic/CRenderTarget::Attach.md)|Adjunta la interfaz de destino de representación existente al objeto|  
|[CRenderTarget::BeginDraw](../Topic/CRenderTarget::BeginDraw.md)|Inicia el dibujo en este destino de representación.|  
|[CRenderTarget::Clear](../Topic/CRenderTarget::Clear.md)|Borra el área de dibujo para el color especificado.|  
|[CRenderTarget::COLORREF\_TO\_D2DCOLOR](../Topic/CRenderTarget::COLORREF_TO_D2DCOLOR.md)|Convierte los valores color GDI y alfa en el objeto D2D1\_COLOR\_F.|  
|[CRenderTarget::CreateCompatibleRenderTarget](../Topic/CRenderTarget::CreateCompatibleRenderTarget.md)|Crea un nuevo destino de representación de mapa de bits para su uso durante el dibujo intermedio fuera de pantalla que es compatible con el destino de representación actual.|  
|[CRenderTarget::Destroy](../Topic/CRenderTarget::Destroy.md)|Elimina uno o más recursos|  
|[CRenderTarget::Detach](../Topic/CRenderTarget::Detach.md)|Desasocia la interfaz de destino de representación del objeto|  
|[CRenderTarget::DrawBitmap](../Topic/CRenderTarget::DrawBitmap.md)|Dibuja el texto con formato descrito por el objeto IDWriteTextLayout especificado.|  
|[CRenderTarget::DrawEllipse](../Topic/CRenderTarget::DrawEllipse.md)|Dibuja el contorno de la elipse especificada utilizando el estilo de trazo especificado.|  
|[CRenderTarget::DrawGeometry](../Topic/CRenderTarget::DrawGeometry.md)|Dibuja el contorno de la geometría especificada utilizando el estilo de trazo especificado.|  
|[CRenderTarget::DrawGlyphRun](../Topic/CRenderTarget::DrawGlyphRun.md)|Dibuja los glifos especificados.|  
|[CRenderTarget::DrawLine](../Topic/CRenderTarget::DrawLine.md)|Dibuja una línea entre los puntos especificados utilizando el estilo de trazo especificado.|  
|[CRenderTarget::DrawRectangle](../Topic/CRenderTarget::DrawRectangle.md)|Dibuja el contorno de un rectángulo que tiene las dimensiones y estilo de trazo especificados.|  
|[CRenderTarget::DrawRoundedRectangle](../Topic/CRenderTarget::DrawRoundedRectangle.md)|Dibuja el contorno de un rectángulo redondeado utilizando el estilo de trazo especificado.|  
|[CRenderTarget::DrawText](../Topic/CRenderTarget::DrawText.md)|Dibuja el texto especificado mediante la información de formato proporcionada por un objeto IDWriteTextFormat.|  
|[CRenderTarget::DrawTextLayout](../Topic/CRenderTarget::DrawTextLayout.md)|Dibuja el texto con formato descrito por el objeto IDWriteTextLayout especificado.|  
|[CRenderTarget::EndDraw](../Topic/CRenderTarget::EndDraw.md)|Finaliza las operaciones del dibujo en el destino de representación e indica el estado del error actual y las etiquetas asociadas.|  
|[CRenderTarget::FillEllipse](../Topic/CRenderTarget::FillEllipse.md)|Pinta el interior de la elipse especificada.|  
|[CRenderTarget::FillGeometry](../Topic/CRenderTarget::FillGeometry.md)|Pinta el interior de la geometría especificada.|  
|[CRenderTarget::FillMesh](../Topic/CRenderTarget::FillMesh.md)|Pinta el interior de la malla especificada.|  
|[CRenderTarget::FillOpacityMask](../Topic/CRenderTarget::FillOpacityMask.md)|Aplica la máscara de opacidad descrita por el mapa de bits especificado a un pincel y utiliza ese pincel para pintar una región del destino de representación.|  
|[CRenderTarget::FillRectangle](../Topic/CRenderTarget::FillRectangle.md)|Pinta el interior del rectángulo especificado.|  
|[CRenderTarget::FillRoundedRectangle](../Topic/CRenderTarget::FillRoundedRectangle.md)|Pinta el interior del rectángulo redondeado especificado.|  
|[CRenderTarget::Flush](../Topic/CRenderTarget::Flush.md)|Ejecuta todos los comandos de dibujo pendientes.|  
|[CRenderTarget::GetAntialiasMode](../Topic/CRenderTarget::GetAntialiasMode.md)|Recupera el modo de suavizado de contorno actual para operaciones de dibujo que no son de texto.|  
|[CRenderTarget::GetDpi](../Topic/CRenderTarget::GetDpi.md)|Devuelve los puntos por pulgada \(PPP\) del destino de representación|  
|[CRenderTarget::GetMaximumBitmapSize](../Topic/CRenderTarget::GetMaximumBitmapSize.md)|Obtiene el tamaño máximo, en unidades dependientes del dispositivo \(píxeles\), de cualquier dimensión de un mapa de bits admitida por el destino de representación|  
|[CRenderTarget::GetPixelFormat](../Topic/CRenderTarget::GetPixelFormat.md)|Recupera el formato de píxel y el modo alfa del destino de representación|  
|[CRenderTarget::GetPixelSize](../Topic/CRenderTarget::GetPixelSize.md)|Devuelve el tamaño del destino de representación en píxeles del dispositivo|  
|[CRenderTarget::GetRenderTarget](../Topic/CRenderTarget::GetRenderTarget.md)|Devuelve la interfaz ID2D1RenderTarget|  
|[CRenderTarget::GetSize](../Topic/CRenderTarget::GetSize.md)|Devuelve el tamaño del destino de representación en píxeles independientes del dispositivo|  
|[CRenderTarget::GetTags](../Topic/CRenderTarget::GetTags.md)|Obtiene la etiqueta para las operaciones posteriores de dibujo.|  
|[CRenderTarget::GetTextAntialiasMode](../Topic/CRenderTarget::GetTextAntialiasMode.md)|Obtiene el modo de suavizado de contorno actual para las operaciones de dibujo de texto y glifo.|  
|[CRenderTarget::GetTextRenderingParams](../Topic/CRenderTarget::GetTextRenderingParams.md)|Recupera opciones de presentación del texto actual del destino de representación.|  
|[CRenderTarget::GetTransform](../Topic/CRenderTarget::GetTransform.md)|Aplica la transformación especificada al destino de representación, reemplazando la transformación existente.  Todas las operaciones de dibujo posteriores se producen en el espacio transformado.|  
|[CRenderTarget::IsSupported](../Topic/CRenderTarget::IsSupported.md)|Indica si el destino de representación admite las propiedades especificadas|  
|[CRenderTarget::IsValid](../Topic/CRenderTarget::IsValid.md)|Comprueba la validez del recurso|  
|[CRenderTarget::PopAxisAlignedClip](../Topic/CRenderTarget::PopAxisAlignedClip.md)|Quita el último clip alineado con el eje del destino de representación.  Después de llamar a este método, el clip multimedia ya no se aplica a las operaciones de dibujo posteriores.|  
|[CRenderTarget::PopLayer](../Topic/CRenderTarget::PopLayer.md)|Detiene las operaciones de redirección de dibujo en el nivel especificado por la última llamada a PushLayer.|  
|[CRenderTarget::PushAxisAlignedClip](../Topic/CRenderTarget::PushAxisAlignedClip.md)|Quita el último clip alineado con el eje del destino de representación.  Después de llamar a este método, el clip multimedia ya no se aplica a las operaciones de dibujo posteriores.|  
|[CRenderTarget::PushLayer](../Topic/CRenderTarget::PushLayer.md)|Agrega el nivel especificado al destino de representación para que reciba todas las operaciones de dibujo posteriores hasta que se llame a PopLayer.|  
|[CRenderTarget::RestoreDrawingState](../Topic/CRenderTarget::RestoreDrawingState.md)|Establece el estado de dibujo del destino de representación al del ID2D1DrawingStateBlock especificado.|  
|[CRenderTarget::SaveDrawingState](../Topic/CRenderTarget::SaveDrawingState.md)|Guarda el estado de dibujo actual en el ID2D1DrawingStateBlock especificado.|  
|[CRenderTarget::SetAntialiasMode](../Topic/CRenderTarget::SetAntialiasMode.md)|Establece el modo de suavizado de contorno del destino de representación.  El modo de suavizado de contorno se aplica a todas las operaciones posteriores de dibujo, excepto en las operaciones de dibujo de texto y glifo.|  
|[CRenderTarget::SetDpi](../Topic/CRenderTarget::SetDpi.md)|Establece los puntos por pulgada de \(PPP\) el destino de representación.|  
|[CRenderTarget::SetTags](../Topic/CRenderTarget::SetTags.md)|Especifica una etiqueta para las operaciones posteriores de dibujo.|  
|[CRenderTarget::SetTextAntialiasMode](../Topic/CRenderTarget::SetTextAntialiasMode.md)|Especifica el modo de suavizado de contorno para utilizar en operaciones posteriores de dibujo y glifo.|  
|[CRenderTarget::SetTextRenderingParams](../Topic/CRenderTarget::SetTextRenderingParams.md)|Especifica las opciones de representación del texto que se van a aplicar a todas las operaciones posteriores de dibujo de texto y glifo.|  
|[CRenderTarget::SetTransform](../Topic/CRenderTarget::SetTransform.md)|Sobrecargado.  Aplica la transformación especificada al destino de representación, reemplazando la transformación existente.  Todas las operaciones de dibujo posteriores se producen en el espacio transformado.|  
  
### Métodos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRenderTarget::VerifyResource](../Topic/CRenderTarget::VerifyResource.md)|Comprueba la validez del objeto CD2DResource; crea el objeto si todavía no existe.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRenderTarget::operator ID2D1RenderTarget\*](../Topic/CRenderTarget::operator%20ID2D1RenderTarget*.md)|Devuelve la interfaz ID2D1RenderTarget|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CRenderTarget::m\_lstResources](../Topic/CRenderTarget::m_lstResources.md)|Una lista de punteros a los objetos CD2DResource.|  
|[CRenderTarget::m\_pRenderTarget](../Topic/CRenderTarget::m_pRenderTarget.md)|Puntero a un objeto ID2D1RenderTarget.|  
|[CRenderTarget::m\_pTextFormatDefault](../Topic/CRenderTarget::m_pTextFormatDefault.md)|Un puntero al objeto CD2DTextFormat que contiene un formato de texto predeterminado.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CRenderTarget](../../mfc/reference/crendertarget-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)