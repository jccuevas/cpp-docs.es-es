---
title: "Selecci&#243;n actual en un control Rich Edit | Microsoft Docs"
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
  - "CRichEditCtrl (clase), selección actual en"
  - "selección actual en CRichEditCtrls"
  - "controles Rich Edit, selección actual en"
  - "selección, actual en CRichEditCtrl"
ms.assetid: f6b2a2b6-5481-4ad3-9720-6dd772ea6fc8
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Selecci&#243;n actual en un control Rich Edit
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El usuario puede seleccionar el texto en un control rich edit \([CRichEditCtrl](../mfc/reference/cricheditctrl-class.md)\) mediante el mouse o el teclado.  La selección actual es el intervalo de caracteres seleccionados, o la posición del punto de inserción si no se selecciona ningún carácter.  Una aplicación puede obtener información sobre la selección actual, establece la selección actual, determina cuando los cambios actuales de selección, y muestra u oculta el resaltado de la selección.  
  
 Para determinar la selección actual en un control rich edit, utilice la función miembro de [GetSel](../Topic/CRichEditCtrl::GetSel.md) .  Para establecer la selección actual, utilice la función miembro de [SetSel](../Topic/CRichEditCtrl::SetSel.md) .  La estructura de [CHARRANGE](http://msdn.microsoft.com/library/windows/desktop/bb787885) se utiliza con estas funciones para especificar un intervalo de caracteres.  Para recuperar información sobre el contenido de la selección actual, puede utilizar la función miembro de [GetSelectionType](../Topic/CRichEditCtrl::GetSelectionType.md) .  
  
 De forma predeterminada, un control rich edit muestra y oculta el resaltado de selección cuando recibe y pierde el foco.  Puede mostrar u ocultar el resaltado de selección en cualquier momento utilizando la función miembro de [HideSelection](../Topic/CRichEditCtrl::HideSelection.md) .  Por ejemplo, una aplicación podría proporcionar un cuadro de diálogo Buscar para buscar texto en un control rich edit.  La aplicación podría seleccionar el texto coincidente sin cerrar el cuadro de diálogo, en este caso debe utilizar `HideSelection` para resaltar la selección.  
  
 Para obtener el texto seleccionado en un control rich edit, utilice la función miembro de [GetSelText](../Topic/CRichEditCtrl::GetSelText.md) .  El texto se copia en la matriz de caracteres especificada.  Debe asegurarse de que la matriz es suficiente para contener el texto seleccionado más un carácter null de terminación.  
  
 Puede buscar una cadena en un control rich edit mediante el miembro de [FindText](../Topic/CRichEditCtrl::FindText.md) que la estructura de El [FINDTEXTEX](http://msdn.microsoft.com/library/windows/desktop/bb787909) de la función utilizada con esta función especifica el intervalo de texto para buscar y la cadena para buscar.  También puede especificar opciones como si la búsqueda distingue entre mayúsculas y minúsculas.  
  
## Vea también  
 [Usar CRichEditCtrl](../mfc/using-cricheditctrl.md)   
 [Controles](../mfc/controls-mfc.md)