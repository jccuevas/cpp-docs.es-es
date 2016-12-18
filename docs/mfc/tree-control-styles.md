---
title: "Estilos de control de &#225;rbol | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "TVS_SINGLEEXPAND"
  - "TVS_LINESATROOT"
  - "TVS_HASBUTTONS"
  - "TVS_NOTOOLTIPS"
  - "TVS_HASLINES"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "CTreeCtrl (clase), estilos"
  - "estilos, CTreeCtrl"
  - "estilos, árbol de control"
  - "controles de árbol, estilos"
  - "TVS_EDITLABELS"
  - "TVS_HASBUTTONS"
  - "TVS_HASLINES"
  - "TVS_LINESATROOT"
  - "TVS_NOTOOLTIPS"
  - "TVS_SINGLEEXPAND"
ms.assetid: f43faebd-a355-479e-888a-bf0673d5e1b4
caps.latest.revision: 11
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Estilos de control de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Los estilos del control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) determinan los aspectos de la apariencia de un control de árbol.  Establece los estilos inicial cuando se crea el control de árbol.  Puede recuperar y cambiar los estilos después de crear el control de árbol mediante las funciones de [GetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633584) y de [SetWindowLong](http://msdn.microsoft.com/library/windows/desktop/ms633591) Windows, especificando **GWL\_STYLE** para el parámetro de `nIndex` .  Para obtener una lista completa de los estilos, vea [Estilos de ventana del control de vista de árbol](http://msdn.microsoft.com/library/windows/desktop/bb760013) en [!INCLUDE[winSDK](../atl/includes/winsdk_md.md)].  
  
 El estilo de **TVS\_HASLINES** mejora la representación gráfica de una jerarquía de control de árbol dibujando las líneas que vinculan elementos secundarios a su elemento primario correspondiente.  Este estilo no vincula los elementos en la raíz de la jerarquía.  Para ello, combinar los estilos de **TVS\_HASLINES** y de **TVS\_LINESATROOT** .  
  
 El usuario puede expandir o contraer la lista de un elemento primario de elementos secundarios haciendo doble clic en el elemento primario.  Un control de árbol que tiene el estilo de **TVS\_SINGLEEXPAND** hace que el elemento que selecciona para expandir y elemento que no está seleccionado contraer.  Si el mouse se utiliza al hacer clic en el elemento seleccionado y cerrar el elemento, se desplegará.  Si solo\- se hace clic en el elemento seleccionado cuando está abierta, se contrae.  
  
 Un control de árbol que tiene el estilo de **TVS\_HASBUTTONS** agrega un botón a la izquierda de cada elemento primario.  El usuario puede hacer clic en el botón para expandir o contraer elementos secundarios como alternativa a hacer doble clic en el elemento primario.  **TVS\_HASBUTTONS** no agregar botones a los elementos en la raíz de la jerarquía.  Para ello, debe combinar **TVS\_HASLINES**, **TVS\_LINESATROOT**, y **TVS\_HASBUTTONS**.  
  
 El estilo de **TVS\_EDITLABELS** permite que el usuario modifique las etiquetas de los elementos del control de árbol.  Para obtener más información sobre las etiquetas de edición, vea [Edición del control de árbol](../mfc/tree-control-label-editing.md) más adelante en este tema.  
  
 El estilo de **TVS\_NOTOOLTIPS** deshabilita la característica automática de información sobre herramientas de controles de vista de árbol.  Esta característica muestra automáticamente una información sobre herramientas, que contiene el título del elemento en el cursor, si el título completo actualmente no está visible.  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)