---
title: "CBrush Class | Microsoft Docs"
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
  - "CBrush"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pinceles, CBrush class"
  - "CBrush class"
ms.assetid: e5ef2c62-dd95-4973-9090-f52f605900e1
caps.latest.revision: 21
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBrush Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula un pincel de la interfaz de dispositivo gráfico de Windows \(GDI\).  
  
## Sintaxis  
  
```  
class CBrush : public CGdiObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBrush::CBrush](../Topic/CBrush::CBrush.md)|Crea un objeto `CBrush`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBrush::CreateBrushIndirect](../Topic/CBrush::CreateBrushIndirect.md)|Inicializa un pincel con el estilo, el color, y el modelo especificado en una estructura de [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) .|  
|[CBrush::CreateDIBPatternBrush](../Topic/CBrush::CreateDIBPatternBrush.md)|Inicializa un pincel con un modelo especificado por un mapa de bits independiente del dispositivo \(DIB\).|  
|[CBrush::CreateHatchBrush](../Topic/CBrush::CreateHatchBrush.md)|Inicializa un pincel con el modelo tramado especificado y color.|  
|[CBrush::CreatePatternBrush](../Topic/CBrush::CreatePatternBrush.md)|Inicializa un pincel con un modelo especificado por un mapa de bits.|  
|[CBrush::CreateSolidBrush](../Topic/CBrush::CreateSolidBrush.md)|Inicializa un pincel con el color sólido especificado.|  
|[CBrush::CreateSysColorBrush](../Topic/CBrush::CreateSysColorBrush.md)|Crea un pincel que es el color predeterminado del sistema.|  
|[CBrush::FromHandle](../Topic/CBrush::FromHandle.md)|Devuelve un puntero a un objeto de `CBrush` cuando se le asigna un identificador a un objeto de Windows `HBRUSH` .|  
|[CBrush::GetLogBrush](../Topic/CBrush::GetLogBrush.md)|obtiene una estructura de [LOGBRUSH](http://msdn.microsoft.com/library/windows/desktop/dd145035) .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBrush::operator HBRUSH](../Topic/CBrush::operator%20HBRUSH.md)|Devuelve el identificador de Windows asociado al objeto de `CBrush` .|  
  
## Comentarios  
 Para utilizar un objeto de `CBrush` , crear un objeto de `CBrush` y pasarlo a cualquier función miembro de `CDC` que requiere un pincel.  
  
 Los pinceles pueden ser sólidos, tramados, o modelados.  
  
 Para obtener más información sobre `CBrush`, vea [objetos gráficos](../../mfc/graphic-objects.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBrush`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo PROPDLG de MFC](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CBitmap Class](../../mfc/reference/cbitmap-class.md)   
 [CDC \(clase\)](../../mfc/reference/cdc-class.md)