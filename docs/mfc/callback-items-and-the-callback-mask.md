---
title: "Elementos de devoluci&#243;n de llamada y m&#225;scara de devoluci&#243;n de llamada | Microsoft Docs"
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
  - "elementos de devolución de llamada de clase CListCtrl"
  - "CListCtrl (clase), elementos de devolución de llamada y máscara de devolución de llamada"
ms.assetid: 67c1f76f-6144-453e-9376-6712f89430ae
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Elementos de devoluci&#243;n de llamada y m&#225;scara de devoluci&#243;n de llamada
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Para cada uno de sus elementos, un control de vista de lista almacena normalmente el texto de la etiqueta, el índice de la lista de imágenes de los iconos de los elementos, y un conjunto de bit marca para el estado del elemento.  Puede definir los elementos como elementos de devolución de llamada, que son útiles si la aplicación almacena ya parte de la información de un elemento.  
  
 Define un elemento como elemento de devolución especificando los valores adecuados para los miembros de `pszText` y de `iImage` de la estructura de **LV\_ITEM** \(vea [CListCtrl::GetItem](../Topic/CListCtrl::GetItem.md)\).  Si la aplicación mantiene el elemento o el texto del subelemento, especifique el valor de **LPSTR\_TEXTCALLBACK** para el miembro de `pszText` .  Si la aplicación realiza el seguimiento del icono del elemento, especifique el valor de **I\_IMAGECALLBACK** para el miembro de `iImage` .  
  
 Además de definir elementos de devolución de llamada, también puede modificar la máscara de devolución de llamada del control.  Esta máscara es un conjunto de marcas de bits que especifican los estados de los elementos para los que la aplicación, en lugar del control, almacena los datos actuales.  Máscara de devolución se aplica a los elementos del control, a diferencia de la designación de elemento de devolución de llamada, que se aplica a un elemento específico.  Máscara de devolución es cero de forma predeterminada, lo que significa que el control sigue todos los estados del elemento.  Para cambiar este comportamiento predeterminado, inicialice la máscara a cualquier combinación de los valores siguientes:  
  
-   el elemento de`LVIS_CUT`The se marca para una operación de cortar y pegar.  
  
-   el elemento de`LVIS_DROPHILITED`The se resalta como destino de arrastrar y colocar.  
  
-   el elemento de`LVIS_FOCUSED`The tiene el foco.  
  
-   se selecciona el elemento de`LVIS_SELECTED`The.  
  
-   La aplicación de**LVIS\_OVERLAYMASK**The almacena el índice de la lista de imágenes de la imagen actual de superposición de cada elemento.  
  
-   La aplicación de**LVIS\_STATEIMAGEMASK**The almacena el índice de la imagen del estado actual de cada elemento.  
  
 Para obtener más información sobre cómo recuperar y establecer esta máscara, vea [CListCtrl::GetCallbackMask](../Topic/CListCtrl::GetCallbackMask.md) y [CListCtrl::SetCallbackMask](../Topic/CListCtrl::SetCallbackMask.md).  
  
## Vea también  
 [Usar CListCtrl](../mfc/using-clistctrl.md)   
 [Controles](../mfc/controls-mfc.md)