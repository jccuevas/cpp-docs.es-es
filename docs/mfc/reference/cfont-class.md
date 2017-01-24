---
title: "CFont Class | Microsoft Docs"
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
  - "CFont"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CFont class"
  - "fuentes, clases MFC"
  - "GDI, font classes"
ms.assetid: 3fad6bfe-d6ce-4ab9-967a-5ce0aa102800
caps.latest.revision: 23
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CFont Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula una fuente de la interfaz de dispositivo \(GDI\) gráfico de Windows y proporciona funciones miembro para manipular la fuente.  
  
## Sintaxis  
  
```  
class CFont : public CGdiObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFont::CFont](../Topic/CFont::CFont.md)|Crea un objeto `CFont`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFont::CreateFont](../Topic/CFont::CreateFont.md)|Inicializa `CFont` con las características especificadas.|  
|[CFont::CreateFontIndirect](../Topic/CFont::CreateFontIndirect.md)|Inicializa un objeto de `CFont` con las características incluidas en una estructura de `LOGFONT` .|  
|[CFont::CreatePointFont](../Topic/CFont::CreatePointFont.md)|Inicializa `CFont` con el alto especificado, medido en décimas de un punto, y el tipo de letra.|  
|[CFont::CreatePointFontIndirect](../Topic/CFont::CreatePointFontIndirect.md)|Igual que `CreateFontIndirect` salvo que el alto de fuente se mide en décimas de un punto en lugar de unidades lógicas.|  
|[CFont::FromHandle](../Topic/CFont::FromHandle.md)|Devuelve un puntero a un objeto de `CFont` cuando se especifica Windows **HFONT**.|  
|[CFont::GetLogFont](../Topic/CFont::GetLogFont.md)|Rellena `LOGFONT` con información sobre la fuente lógica asociada al objeto de `CFont` .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CFont::operator HFONT](../Topic/CFont::operator%20HFONT.md)|Devuelve el identificador de la fuente de Windows GDI asociado al objeto de `CFont` .|  
  
## Comentarios  
 Para utilizar un objeto de `CFont` , crear un objeto de `CFont` y asociarlo a una fuente de Windows en ella con [CreateFont](../Topic/CFont::CreateFont.md), [CreateFontIndirect](../Topic/CFont::CreateFontIndirect.md), [CreatePointFont](../Topic/CFont::CreatePointFont.md), o [CreatePointFontIndirect](../Topic/CFont::CreatePointFontIndirect.md), y luego utilizar el miembro del objeto funciona para manipular la fuente.  
  
 Las funciones de `CreatePointFont` y de `CreatePointFontIndirect` son a menudo más fáciles de utilizar que `CreateFont` o `CreateFontIndirect` puesto que haga la conversión del alto de la fuente de un tamaño en puntos en unidades lógicas automáticamente.  
  
 Para obtener más información sobre `CFont`, vea [objetos gráficos](../../mfc/graphic-objects.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CFont`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo HIERSVR de MFC](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)