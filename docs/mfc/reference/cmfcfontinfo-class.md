---
title: "CMFCFontInfo Class | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "reference"
f1_keywords: 
  - "CMFCFontInfo"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CMFCFontInfo class"
  - "CMFCFontInfo::CMFCFontInfo constructor"
ms.assetid: f88329b2-d74e-4921-9441-a3bb6536a049
caps.latest.revision: 26
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 28
---
# CMFCFontInfo Class
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la clase de `CMFCFontInfo` describe el nombre y otros atributos de una fuente.  
  
## Sintaxis  
  
```  
class CMFCFontInfo : public CObject  
```  
  
## Members  
  
### Constructores públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|`CMFCFontInfo`|Crea un objeto `CMFCFontInfo`.|  
  
### Métodos públicos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCFontInfo::GetFullName](../Topic/CMFCFontInfo::GetFullName.md)|Recupera los nombres concatenados de una fuente y del juego de caracteres \(script\).|  
  
### miembros de datos  
  
|Name|Descripción|  
|----------|-----------------|  
|[CMFCFontInfo::m\_nCharSet](../Topic/CMFCFontInfo::m_nCharSet.md)|un valor que especifica el juego de caracteres \(script\) asociado con la fuente.|  
|[CMFCFontInfo::m\_nPitchAndFamily](../Topic/CMFCFontInfo::m_nPitchAndFamily.md)|Un valor que especifica el paso y la familia de fuentes.|  
|[CMFCFontInfo::m\_nType](../Topic/CMFCFontInfo::m_nType.md)|un valor que especifica el tipo de la fuente.|  
|[CMFCFontInfo::m\_strName](../Topic/CMFCFontInfo::m_strName.md)|el nombre de la fuente; por ejemplo, **arial**.|  
|[CMFCFontInfo::m\_strScript](../Topic/CMFCFontInfo::m_strScript.md)|el nombre de un juego de caracteres \(script\) asociado con la fuente.|  
  
## Comentarios  
 Puede adjuntar un objeto de `CMFCFontInfo` a un elemento de la clase de [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md) .  Llame al método de [CMFCToolBarFontComboBox::GetFontDesc](../Topic/CMFCToolBarFontComboBox::GetFontDesc.md) para recuperar un puntero a un objeto de `CMFCFontInfo` .  
  
## Ejemplo  
 El ejemplo siguiente se muestra cómo utilizar los diversos miembros de la clase de `CMFCFontInfo` .  El ejemplo muestra cómo obtener un objeto de `CMFCFontInfo` de `CMFCRibbonFontComboBox`, y cómo tener acceso a las variables locales.  Este ejemplo forma parte de [Ejemplo 2007 de demostración de MS\-Office](../../top/visual-cpp-samples.md).  
  
 [!code-cpp[NVC_MFC_MSOffice2007Demo#6](../../mfc/reference/codesnippet/CPP/cmfcfontinfo-class_1.cpp)]  
  
## Requisitos  
 **encabezado:** afxtoolbarfontcombobox.h  
  
## Vea también  
 [Gráfico de jerarquías](../../mfc/hierarchy-chart.md)   
 [Clases](../../mfc/reference/mfc-classes.md)   
 [CMFCToolBarFontComboBox Class](../../mfc/reference/cmfctoolbarfontcombobox-class.md)   
 [CMFCToolBarFontSizeComboBox Class](../../mfc/reference/cmfctoolbarfontsizecombobox-class.md)