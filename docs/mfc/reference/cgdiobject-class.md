---
title: "CGdiObject Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CGdiObject"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "pinceles, base class for"
  - "CGdiObject class"
  - "fuentes, base class for"
  - "objetos GDI, base class for"
  - "paletas, base class for"
  - "lápices, base class for"
  - "regiones, base class for"
ms.assetid: 1cba3ba5-3d49-4e43-8293-209299f2f6f4
caps.latest.revision: 21
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 23
---
# CGdiObject Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Proporciona una clase base para las clases diferentes de objetos de la interfaz de dispositivo \(GDI\) gráfico de Windows como mapas de bits, regiones, pinceles, lápices, tablas, y fuentes.  
  
## Sintaxis  
  
```  
class CGdiObject : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGdiObject::CGdiObject](../Topic/CGdiObject::CGdiObject.md)|Crea un objeto `CGdiObject`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGdiObject::Attach](../Topic/CGdiObject::Attach.md)|Asocia un objeto de Windows GDI a un objeto de `CGdiObject` .|  
|[CGdiObject::CreateStockObject](../Topic/CGdiObject::CreateStockObject.md)|Recupera un identificador a una de lápices, de los pinceles, o de fuentes comunes predefinidos Windows.|  
|[CGdiObject::DeleteObject](../Topic/CGdiObject::DeleteObject.md)|Elimina el objeto de Windows GDI asociado al objeto de `CGdiObject` de memoria y todo el almacenamiento del sistema asociados al objeto.|  
|[CGdiObject::DeleteTempMap](../Topic/CGdiObject::DeleteTempMap.md)|Elimina cualquier objeto temporal de `CGdiObject` creado por `FromHandle`.|  
|[CGdiObject::Detach](../Topic/CGdiObject::Detach.md)|Desasocia un objeto de Windows GDI de un objeto de `CGdiObject` y devuelve un identificador para el objeto de Windows GDI.|  
|[CGdiObject::FromHandle](../Topic/CGdiObject::FromHandle.md)|devuelve un puntero a un objeto de `CGdiObject` dado un identificador a un objeto de Windows GDI.|  
|[CGdiObject::GetObject](../Topic/CGdiObject::GetObject.md)|Rellena un búfer con datos que describe el objeto de Windows GDI asociado al objeto de `CGdiObject` .|  
|[CGdiObject::GetObjectType](../Topic/CGdiObject::GetObjectType.md)|Recupera el tipo de objeto de GDI.|  
|[CGdiObject::GetSafeHandle](../Topic/CGdiObject::GetSafeHandle.md)|Devuelve `m_hObject` a menos que `this` es `NULL`, en cuyo caso se devuelve `NULL` .|  
|[CGdiObject::UnrealizeObject](../Topic/CGdiObject::UnrealizeObject.md)|Restablece el origen de un pincel o restaura una paleta lógica.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGdiObject::operator \!\=](../Topic/CGdiObject::operator%20!=.md)|Determina si dos objetos de GDI no son lógicamente iguales.|  
|[CGdiObject::operator \=\=](../Topic/CGdiObject::operator%20==.md)|determina si dos objetos de GDI son lógicamente iguales.|  
|[CGdiObject::operator HGDIOBJ](../Topic/CGdiObject::operator%20HGDIOBJ.md)|Recupera `HANDLE` al objeto asociado de Windows GDI.|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CGdiObject::m\_hObject](../Topic/CGdiObject::m_hObject.md)|`HANDLE` que contiene `HBITMAP`, `HPALETTE`, `HRGN`, `HBRUSH`, `HPEN`, o `HFONT` asociado a este objeto.|  
  
## Comentarios  
 Nunca se crea `CGdiObject` directamente.  En su lugar, se crea un objeto a partir de una de sus clases derivadas, como `CPen` o `CBrush`.  
  
 Para obtener más información sobre `CGdiObject`, vea [Objetos gráficos](../../mfc/graphic-objects.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 `CGdiObject`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CBitmap Class](../../mfc/reference/cbitmap-class.md)   
 [CBrush Class](../../mfc/reference/cbrush-class.md)   
 [CFont Class](../../mfc/reference/cfont-class.md)   
 [CPalette Class](../../mfc/reference/cpalette-class.md)   
 [CPen Class](../../mfc/reference/cpen-class.md)   
 [CRgn \(clase\)](../../mfc/reference/crgn-class.md)