---
title: "Formato de p&#225;rrafo en los controles Rich Edit | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CRichEditCtrl (clase), aplicar formato de párrafo en"
  - "aplicar formato [C++], párrafos"
  - "aplicar formato de párrafo en CRichEditCtrl"
  - "controles Rich Edit, aplicar formato de párrafo en"
ms.assetid: 0df2e4c9-2074-4e41-b913-87cb8c1b4d43
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Formato de p&#225;rrafo en los controles Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Puede utilizar funciones miembro de control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) para dar formato a los párrafos y recuperar información de formato.  Los atributos de formato de párrafo incluyen la alineación, fichas, las sangrías, y la numeración.  
  
 Puede aplicar formato de párrafo utilizando la función miembro de [SetParaFormat](../Topic/CRichEditCtrl::SetParaFormat.md) .  Para determinar el formato de párrafo actual para el texto seleccionado, utilice la función miembro de [GetParaFormat](../Topic/CRichEditCtrl::GetParaFormat.md) .  La estructura de [PARAFORMAT](http://msdn.microsoft.com/library/windows/desktop/bb787940) se utiliza con estas funciones miembro para especificar atributos de párrafo.  Uno de los miembros importantes de **PARAFORMAT** es **dwMask**.  En `SetParaFormat`, **dwMask** especifica que los atributos de párrafo se establecidos por esta llamada de función.  informes de`GetParaFormat` los atributos del primer párrafo de la selección; **dwMask** especifica los atributos que son coherentes en la selección.  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)