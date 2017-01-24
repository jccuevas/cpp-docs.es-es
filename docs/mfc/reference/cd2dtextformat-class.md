---
title: "CD2DTextFormat (Clase) | Microsoft Docs"
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
  - "afxrendertarget/CD2DTextFormat"
  - "CD2DTextFormat"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CD2DTextFormat (clase)"
ms.assetid: db194cec-9dae-4644-ab84-7c43b7164117
caps.latest.revision: 16
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# CD2DTextFormat (Clase)
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Contenedor para IDWriteTextFormat.  
  
## Sintaxis  
  
```  
class CD2DTextFormat : public CD2DResource;  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DTextFormat::CD2DTextFormat](../Topic/CD2DTextFormat::CD2DTextFormat.md)|Construye un objeto CD2DTextFormat.|  
|[CD2DTextFormat::~CD2DTextFormat](../Topic/CD2DTextFormat::~CD2DTextFormat.md)|El destructor.  Se llama cuando se destruye un objeto de formato de texto D2D.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DTextFormat::Create](../Topic/CD2DTextFormat::Create.md)|Crea un CD2DTextFormat.  \(Invalida [CD2DResource::Create](../Topic/CD2DResource::Create.md).\)|  
|[CD2DTextFormat::Destroy](../Topic/CD2DTextFormat::Destroy.md)|Destruye un objeto CD2DTextFormat.  \(Invalida [CD2DResource::Destroy](../Topic/CD2DResource::Destroy.md).\)|  
|[CD2DTextFormat::Get](../Topic/CD2DTextFormat::Get.md)|Devuelve la interfaz IDWriteTextFormat|  
|[CD2DTextFormat::GetFontFamilyName](../Topic/CD2DTextFormat::GetFontFamilyName.md)|Obtiene una copia del nombre de la familia de fuentes.|  
|[CD2DTextFormat::GetLocaleName](../Topic/CD2DTextFormat::GetLocaleName.md)|Obtiene una copia del nombre de la configuración regional.|  
|[CD2DTextFormat::IsValid](../Topic/CD2DTextFormat::IsValid.md)|Comprueba la validez del recurso \(invalida [CD2DResource::IsValid](../Topic/CD2DResource::IsValid.md)\).|  
|[CD2DTextFormat::ReCreate](../Topic/CD2DTextFormat::ReCreate.md)|Vuelve a crear un CD2DTextFormat.  \(Invalida [CD2DResource::ReCreate](../Topic/CD2DResource::ReCreate.md).\)|  
  
### Operadores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DTextFormat::operator IDWriteTextFormat\*](../Topic/CD2DTextFormat::operator%20IDWriteTextFormat*.md)|Devuelve la interfaz IDWriteTextFormat|  
  
### Miembros de datos protegidos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CD2DTextFormat::m\_pTextFormat](../Topic/CD2DTextFormat::m_pTextFormat.md)|Puntero a IDWriteTextFormat.|  
  
## Jerarquía de herencia  
 [CObject](../../mfc/reference/cobject-class.md)  
  
 [CD2DResource](../../mfc/reference/cd2dresource-class.md)  
  
 [CD2DTextFormat](../../mfc/reference/cd2dtextformat-class.md)  
  
## Requisitos  
 **Encabezado:** afxrendertarget.h  
  
## Vea también  
 [Clases](../../mfc/reference/mfc-classes.md)