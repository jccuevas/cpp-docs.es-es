---
title: "CPalette Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CPalette"
  - "HPALETTE"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "paletas de colores, MFC"
  - "CPalette class"
  - "HPALETTE"
ms.assetid: 8cd95498-53ed-4852-85e1-70e522541114
caps.latest.revision: 23
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 25
---
# CPalette Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

encapsula una paleta de colores de Windows.  
  
## Sintaxis  
  
```  
class CPalette : public CGdiObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPalette::CPalette](../Topic/CPalette::CPalette.md)|Construye un objeto de `CPalette` sin la paleta asociada de Windows.  Debe inicializar el objeto de `CPalette` con una de las funciones miembro de inicialización antes de poderse utilizar.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPalette::AnimatePalette](../Topic/CPalette::AnimatePalette.md)|reemplaza entradas en la paleta lógica identificada por el objeto de `CPalette` .  La aplicación no tiene que actualizar el área cliente, porque Windows asigna las nuevas entradas en la tabla del sistema inmediatamente.|  
|[CPalette::CreateHalftonePalette](../Topic/CPalette::CreateHalftonePalette.md)|Crea una tabla de semitono para el contexto del dispositivo y la agrega al objeto de `CPalette` .|  
|[CPalette::CreatePalette](../Topic/CPalette::CreatePalette.md)|Crea una tabla de colores de Windows y la agrega al objeto de `CPalette` .|  
|[CPalette::FromHandle](../Topic/CPalette::FromHandle.md)|Devuelve un puntero a un objeto de `CPalette` cuando se le asigna un identificador a un objeto de la tabla de Windows.|  
|[CPalette::GetEntryCount](../Topic/CPalette::GetEntryCount.md)|Recupera el número de entradas de la tabla en una tabla lógica.|  
|[CPalette::GetNearestPaletteIndex](../Topic/CPalette::GetNearestPaletteIndex.md)|Devuelve el índice de la entrada en la paleta lógica que más se aproxime a un valor de color.|  
|[CPalette::GetPaletteEntries](../Topic/CPalette::GetPaletteEntries.md)|Recupera un intervalo de las entradas de la tabla en una tabla lógica.|  
|[CPalette::ResizePalette](../Topic/CPalette::ResizePalette.md)|Cambia el tamaño de la paleta lógica especificada por el objeto de `CPalette` el número especificado de entradas.|  
|[CPalette::SetPaletteEntries](../Topic/CPalette::SetPaletteEntries.md)|Establece los valores de color RGB y marca en un intervalo de entradas en una paleta lógica.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPalette::operator HPALETTE](../Topic/CPalette::operator%20HPALETTE.md)|Devuelve `HPALETTE` asociado a `CPalette`.|  
  
## Comentarios  
 Una paleta proporciona una interfaz entre una aplicación y un dispositivo de salida de color \(como un dispositivo de pantalla\).  La interfaz permite a la aplicación para aprovechar totalmente las capacidades de color del dispositivo de salida sin gravemente la interferencia con los colores presentados por otras aplicaciones.  Windows utiliza la paleta lógica de la aplicación \(una lista de colores necesarios\) y la tabla del sistema \(definir colores disponibles\) para determinar los colores utilizados.  
  
 Un objeto de `CPalette` proporciona funciones miembro para manipular la paleta denominada por el objeto.  Crea un objeto de `CPalette` y utilice las funciones miembro para crear la tabla real, un objeto de la interfaz de \(GDI\) dispositivo gráfico, y manipular sus entradas y otras propiedades.  
  
 Para obtener más información sobre cómo utilizar `CPalette`, vea [objetos gráficos](../../mfc/graphic-objects.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPalette`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo DIBLOOK de MFC](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CPalette::GetPaletteEntries](../Topic/CPalette::GetPaletteEntries.md)   
 [CPalette::SetPaletteEntries](../Topic/CPalette::SetPaletteEntries.md)