---
title: "CFontHolder Class | Microsoft Docs"
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
  - "CFontHolder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFontHolder class"
  - "custom fonts"
  - "fuentes, controles ActiveX"
ms.assetid: 728ab472-0c97-440d-889f-1324c6e1b6b8
caps.latest.revision: 19
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFontHolder Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa la propiedad de fuente común y encapsula la funcionalidad de un objeto de fuente de Windows y de la interfaz de `IFont` .  
  
## Sintaxis  
  
```  
class CFontHolder  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontHolder::CFontHolder](../Topic/CFontHolder::CFontHolder.md)|Crea un objeto `CFontHolder`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontHolder::GetDisplayString](../Topic/CFontHolder::GetDisplayString.md)|Recupera la cadena que se muestra en el explorador de propiedades de un contenedor.|  
|[CFontHolder::GetFontDispatch](../Topic/CFontHolder::GetFontDispatch.md)|Devuelve la interfaz de `IDispatch` de fuente.|  
|[CFontHolder::GetFontHandle](../Topic/CFontHolder::GetFontHandle.md)|devuelve un identificador a una fuente de Windows.|  
|[CFontHolder::InitializeFont](../Topic/CFontHolder::InitializeFont.md)|Inicializa un objeto de `CFontHolder` .|  
|[CFontHolder::QueryTextMetrics](../Topic/CFontHolder::QueryTextMetrics.md)|Recupera información para la fuente relacionada.|  
|[CFontHolder::ReleaseFont](../Topic/CFontHolder::ReleaseFont.md)|Desconecta el objeto de `CFontHolder` de las interfaces de `IFont` y de `IFontNotification` .|  
|[CFontHolder::Select](../Topic/CFontHolder::Select.md)|Seleccione un recurso de fuente en un contexto de dispositivo.|  
|[CFontHolder::SetFont](../Topic/CFontHolder::SetFont.md)|conecta el objeto de `CFontHolder` a una interfaz de `IFont` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFontHolder::m\_pFont](../Topic/CFontHolder::m_pFont.md)|Un puntero a la interfaz de `IFont` del objeto de `CFontHolder` .|  
  
## Comentarios  
 `CFontHolder` no tiene una clase base.  
  
 Utilice esta clase para implementar propiedades de fuentes personalizadas para el control.  Para obtener información sobre cómo crear propiedades, vea el artículo [Controles ActiveX: Utilizar las fuentes](../../mfc/mfc-activex-controls-using-fonts.md).  
  
## Jerarquía de herencia  
 `CFontHolder`  
  
## Requisitos  
 **encabezado:** afxctl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPropExchange Class](../../mfc/reference/cpropexchange-class.md)