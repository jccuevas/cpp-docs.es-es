---
title: "Usar controles de &#225;rbol | Microsoft Docs"
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
  - "CTreeCtrl (clase), utilizar"
  - "controles de árbol, acerca de los controles de árbol"
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
caps.latest.revision: 10
caps.handback.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Usar controles de &#225;rbol
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El uso típico de un control de árbol \([CTreeCtrl](../mfc/reference/ctreectrl-class.md)\) sigue el modelo siguiente:  
  
-   Se crea el control.  Si el control se especifica en una plantilla de cuadro de diálogo o si usa `CTreeView`, creación es automática cuando se crea el cuadro de diálogo o la vista.  Si desea crear el control de árbol como una ventana secundaria de alguna otra ventana, utilice la función miembro de [crear](../Topic/CTreeCtrl::Create.md) .  
  
-   Si desea que el control de árbol para utilizar imágenes, establezca una imagen lista llamando a [SetImageList](../Topic/CTreeCtrl::SetImageList.md).  También puede cambiar la sangría llamando a [SetIndent](../Topic/CTreeCtrl::SetIndent.md).  Un buen momento para ello está en [OnInitDialog](../Topic/CDialog::OnInitDialog.md) \(para los controles de cuadros de diálogo\) o [OnInitialUpdate](../Topic/CView::OnInitialUpdate.md) \(para las vistas\).  
  
-   Escribe los datos en el control llamando a la función de `CTreeCtrl`[InsertItem](../Topic/CTreeCtrl::InsertItem.md) una vez para cada elemento de datos.  `InsertItem` devuelve un identificador al elemento que puede utilizar para hacer referencia a él más adelante, por ejemplo al agregar elementos secundarios.  Un buen momento para inicializar los datos está en `OnInitDialog` \(para los controles de cuadros de diálogo\) o `OnInitialUpdate` \(para las vistas\).  
  
-   Cuando el usuario interactúa con el control, enviará distintos mensajes de notificación.  Puede especificar una función para tratar cada uno de los mensajes que desea controlar agregando una macro de **ON\_NOTIFY\_REFLECT** en el mapa de mensajes de la ventana de control o agregando una macro de `ON_NOTIFY` al mapa de mensajes de la ventana primaria.  Vea [Mensajes de notificación del control de árbol](../mfc/tree-control-notification-messages.md) más adelante en este tema para obtener una lista de notificaciones posibles.  
  
-   Llame a las distintas funciones específicas de miembro para establecer los valores del control.  Los cambios que puede realizar incluyen que establece la sangría y que cambia el texto, la imagen, o los datos asociados a un elemento.  
  
-   Utilice otro get funciones para examinar el contenido del control.  También puede recorrer el contenido del control de árbol con funciones que permiten recuperar identificadores a los elementos primarios, los elementos secundarios, y los elementos relacionados de un elemento especificado.  Incluso puede ordenar los elementos secundarios de un nodo determinado.  
  
-   Cuando se hace con el control, asegúrese de que esté destruido correctamente.  Si el control de árbol está en un cuadro de diálogo o si es una vista, éste y el objeto de `CTreeCtrl` se destruyeron automáticamente.  Si no, deberá asegurarse de que el control y el objeto de `CTreeCtrl` están destruirse correctamente.  
  
## Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)