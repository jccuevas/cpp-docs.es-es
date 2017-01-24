---
title: "CPictureHolder Class | Microsoft Docs"
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
  - "Picture"
  - "CPictureHolder"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "controles [MFC], OLE"
  - "CPictureHolder class"
  - "controles OLE, imagen"
  - "Picture property"
ms.assetid: a4f59775-704a-41dd-b5bd-2e531c95127a
caps.latest.revision: 20
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CPictureHolder Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Implementa una propiedad de imagen, que permite que el usuario muestre una imagen en el control.  
  
## Sintaxis  
  
```  
class CPictureHolder  
```  
  
## Miembros  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPictureHolder::CPictureHolder](../Topic/CPictureHolder::CPictureHolder.md)|Crea un objeto `CPictureHolder`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPictureHolder::CreateEmpty](../Topic/CPictureHolder::CreateEmpty.md)|Crea un objeto `CPictureHolder` vacío.|  
|[CPictureHolder::CreateFromBitmap](../Topic/CPictureHolder::CreateFromBitmap.md)|crea un objeto de `CPictureHolder` de un mapa de bits.|  
|[CPictureHolder::CreateFromIcon](../Topic/CPictureHolder::CreateFromIcon.md)|crea un objeto de `CPictureHolder` de un icono.|  
|[CPictureHolder::CreateFromMetafile](../Topic/CPictureHolder::CreateFromMetafile.md)|crea un objeto de `CPictureHolder` de un metarchivo.|  
|[CPictureHolder::GetDisplayString](../Topic/CPictureHolder::GetDisplayString.md)|Recupera la cadena que se muestra en el explorador de propiedades de un contenedor de controles.|  
|[CPictureHolder::GetPictureDispatch](../Topic/CPictureHolder::GetPictureDispatch.md)|Devuelve la interfaz de `IDispatch` del objeto de `CPictureHolder` .|  
|[CPictureHolder::GetType](../Topic/CPictureHolder::GetType.md)|Indica si el objeto de `CPictureHolder` es un mapa de bits, un metarchivo, o icono.|  
|[CPictureHolder::Render](../Topic/CPictureHolder::Render.md)|genera la imagen.|  
|[CPictureHolder::SetPictureDispatch](../Topic/CPictureHolder::SetPictureDispatch.md)|Establece la interfaz de `IDispatch` del objeto de `CPictureHolder` .|  
  
### Miembros de datos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CPictureHolder::m\_pPict](../Topic/CPictureHolder::m_pPict.md)|Un puntero a un objeto de imagen.|  
  
## Comentarios  
 `CPictureHolder` no tiene una clase base.  
  
 Con la propiedad de imagen común, el programador puede especificar un mapa de bits, un icono, o un metarchivo para la presentación.  
  
 Para obtener información sobre cómo crear propiedades de imágenes personalizadas, vea el artículo [Controles ActiveX de MFC: Mediante las imágenes en un control ActiveX](../../mfc/mfc-activex-controls-using-pictures-in-an-activex-control.md).  
  
## Jerarquía de herencia  
 `CPictureHolder`  
  
## Requisitos  
 **encabezado:** afxctl.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [CFontHolder Class](../../mfc/reference/cfontholder-class.md)