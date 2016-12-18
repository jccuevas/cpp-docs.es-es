---
title: "CD2DTextLayout (Clase) | Microsoft Docs"
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
  - "CD2DTextLayout"
  - "afxrendertarget/CD2DTextLayout"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DTextLayout (clase)"
ms.assetid: 724bd13c-f2ef-4e55-a775-8cb04b7b7908
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DTextLayout (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para IDWriteTextLayout.  
  
## Sintaxis  
  
```  
class CD2DTextLayout : public CD2DResource;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DTextLayout::CD2DTextLayout](../Topic/CD2DTextLayout::CD2DTextLayout.md)|Construye un objeto CD2DTextLayout.|  
|[CD2DTextLayout::~CD2DTextLayout](../Topic/CD2DTextLayout::~CD2DTextLayout.md)|El destructor.  Se llama cuando se destruye un objeto de formato de texto D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DTextLayout::Create](../Topic/CD2DTextLayout::Create.md)|Crea un CD2DTextLayout.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DTextLayout::Destroy](../Topic/CD2DTextLayout::Destroy.md)|Destruye un objeto CD2DTextLayout.  \(Invalida [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md).\)|  
|[CD2DTextLayout::Get](../Topic/CD2DTextLayout::Get.md)|Devuelve la interfaz IDWriteTextLayout|  
|[CD2DTextLayout::GetFontFamilyName](../Topic/CD2DTextLayout::GetFontFamilyName.md)|Copia el nombre de la familia de fuentes del texto en la posición especificada.|  
|[CD2DTextLayout::GetLocaleName](../Topic/CD2DTextLayout::GetLocaleName.md)|Obtiene el nombre de configuración regional de la posición del texto especificado.|  
|[CD2DTextLayout::IsValid](../Topic/CD2DTextLayout::IsValid.md)|Comprueba la validez del recurso \(invalida [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\).|  
|[CD2DTextLayout::ReCreate](../Topic/CD2DTextLayout::ReCreate.md)|Vuelve a crear un CD2DTextLayout.  \(Invalida [CD2DResource::ReCreate](../Topic/CD2DResource::ReCreate.md).\)|  
|[CD2DTextLayout::SetFontFamilyName](../Topic/CD2DTextLayout::SetFontFamilyName.md)|Establece el nombre de la familia de fuentes terminado en null para el texto dentro de un rango de texto especificado|  
|[CD2DTextLayout::SetLocaleName](../Topic/CD2DTextLayout::SetLocaleName.md)|Establece el nombre de la configuración regional para el texto dentro de un rango de texto especificado|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DTextLayout::operator IDWriteTextLayout\*](../Topic/CD2DTextLayout::operator%20IDWriteTextLayout*.md)|Devuelve la interfaz IDWriteTextLayout|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DTextLayout::m\_pTextLayout](../Topic/CD2DTextLayout::m_pTextLayout.md)|Puntero a IDWriteTextLayout.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextLayout](../../mfc/reference/cd2dtextlayout-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)