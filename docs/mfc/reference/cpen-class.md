---
title: "CPen Class | Microsoft Docs"
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
  - "HPEN"
  - "CPen"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CPen class"
  - "HPEN"
  - "lápices, MFC"
ms.assetid: 93175a3a-d46c-4768-be8d-863254f97a5f
caps.latest.revision: 20
caps.handback.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPen Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula un lápiz de la interfaz de dispositivo gráfico de Windows \(GDI\).  
  
## Sintaxis  
  
```  
class CPen : public CGdiObject  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPen::CPen](../Topic/CPen::CPen.md)|Crea un objeto `CPen`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPen::CreatePen](../Topic/CPen::CreatePen.md)|Crea un cosmético lógico o un lápiz geométricos con el estilo, el ancho, y los atributos especificados del pincel, y lo asocia al objeto de `CPen` .|  
|[CPen::CreatePenIndirect](../Topic/CPen::CreatePenIndirect.md)|Crea un lápiz con el estilo, el ancho, y color determinado en una estructura de [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) , y lo asocia al objeto de `CPen` .|  
|[CPen::FromHandle](../Topic/CPen::FromHandle.md)|Devuelve un puntero a un objeto de `CPen` cuando se especifica Windows `HPEN`.|  
|[CPen::GetExtLogPen](../Topic/CPen::GetExtLogPen.md)|obtiene una estructura subyacente de [EXTLOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd162711) .|  
|[CPen::GetLogPen](../Topic/CPen::GetLogPen.md)|obtiene una estructura subyacente de [LOGPEN](http://msdn.microsoft.com/library/windows/desktop/dd145041) .|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPen::operator HPEN](../Topic/CPen::operator%20HPEN.md)|Devuelve el identificador de Windows asociado al objeto de `CPen` .|  
  
## Comentarios  
 Para obtener más información sobre cómo utilizar `CPen`, vea [objetos gráficos](../../mfc/graphic-objects.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CPen`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CBrush Class](../../mfc/reference/cbrush-class.md)