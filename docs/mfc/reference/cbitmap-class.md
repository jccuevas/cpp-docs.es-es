---
title: "CBitmap Class | Microsoft Docs"
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
  - "CBitmap"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CBitmap class"
  - "dibujar, herramientas"
  - "GDI bitmap"
ms.assetid: 3980616a-c59d-495a-86e6-62bd3889c84c
caps.latest.revision: 22
caps.handback.revision: 11
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CBitmap Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Encapsula un mapa de bits de la interfaz de dispositivo \(GDI\) gráfico de Windows y proporciona funciones miembro para manipular el mapa de bits.  
  
## Sintaxis  
  
```  
class CBitmap : public CGdiObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmap::CBitmap](../Topic/CBitmap::CBitmap.md)|Crea un objeto `CBitmap`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmap::CreateBitmap](../Topic/CBitmap::CreateBitmap.md)|Inicializa el objeto con un mapa de bits dispositivo\- dependiente de memoria con un ancho especificado, un alto, y una configuración de bits.|  
|[CBitmap::CreateBitmapIndirect](../Topic/CBitmap::CreateBitmapIndirect.md)|Inicializa el objeto con un mapa de bits con el ancho, alto, y la configuración de bits \(si se especifica uno\) especificada en una estructura de **BITMAP** .|  
|[CBitmap::CreateCompatibleBitmap](../Topic/CBitmap::CreateCompatibleBitmap.md)|Inicializa el objeto con un mapa de bits de modo compatible con el dispositivo especificado.|  
|[CBitmap::CreateDiscardableBitmap](../Topic/CBitmap::CreateDiscardableBitmap.md)|Inicializa el objeto con un mapa de bits discardable compatible con el dispositivo especificado.|  
|[CBitmap::FromHandle](../Topic/CBitmap::FromHandle.md)|Devuelve un puntero a un objeto de `CBitmap` cuando se le asigna un identificador a un mapa de bits de Windows `HBITMAP` .|  
|[CBitmap::GetBitmap](../Topic/CBitmap::GetBitmap.md)|Rellena una estructura de **BITMAP** con la información del mapa de bits.|  
|[CBitmap::GetBitmapBits](../Topic/CBitmap::GetBitmapBits.md)|Copia los bits del mapa de bits especificado en el búfer especificado.|  
|[CBitmap::GetBitmapDimension](../Topic/CBitmap::GetBitmapDimension.md)|Devuelve el ancho y el alto del mapa de bits.  El alto y el ancho se supone que se ha establecido previamente por la función miembro de [SetBitmapDimension](../Topic/CBitmap::SetBitmapDimension.md) .|  
|[CBitmap::LoadBitmap](../Topic/CBitmap::LoadBitmap.md)|Inicializa el objeto cargando un recurso bitmap denominado del archivo ejecutable de la aplicación y asociar el mapa de bits al objeto.|  
|[CBitmap::LoadMappedBitmap](../Topic/CBitmap::LoadMappedBitmap.md)|Carga un mapa de bits y colores de mapas a los colores del sistema actual.|  
|[CBitmap::LoadOEMBitmap](../Topic/CBitmap::LoadOEMBitmap.md)|Inicializa el objeto cargando un mapa de bits de Windows predefinido y asociar el mapa de bits al objeto.|  
|[CBitmap::SetBitmapBits](../Topic/CBitmap::SetBitmapBits.md)|Establece los bits de un mapa de bits con los valores de bit especificados.|  
|[CBitmap::SetBitmapDimension](../Topic/CBitmap::SetBitmapDimension.md)|Asigna un ancho y alto en un mapa de bits en unidades de 0,1 milímetros.|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CBitmap::operator HBITMAP](../Topic/CBitmap::operator%20HBITMAP.md)|Devuelve el identificador de Windows asociado al objeto de `CBitmap` .|  
  
## Comentarios  
 Para utilizar un objeto de `CBitmap` , cree el objeto, adjunte un identificador bitmap a con una de las funciones miembro de inicialización, y después llama a las funciones miembro del objeto.  
  
 Para obtener más información sobre cómo utilizar objetos gráficos o error de `CBitmap`, vea [objetos gráficos](../../mfc/graphic-objects.md).  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CGdiObject](../../mfc/reference/cgdiobject-class.md)  
  
 `CBitmap`  
  
## Requisitos  
 **Encabezado:** afxwin.h  
  
## Vea también  
 [ejemplo MDI de MFC](../../top/visual-cpp-samples.md)   
 [CGdiObject Class](../../mfc/reference/cgdiobject-class.md)   
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)