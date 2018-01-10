---
title: "Usar controles de árbol | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- CTreeCtrl class [MFC], using
- tree controls [MFC], about tree controls
ms.assetid: 4e92941a-e477-4fb1-b1ce-4abeafbef1c1
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: ea3b7e0348cb21aa4338293f7cc1119e380f92dc
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="using-tree-controls"></a>Usar controles de árbol
Uso típico de un control de árbol ([CTreeCtrl](../mfc/reference/ctreectrl-class.md)) sigue el modelo siguiente:  
  
-   Se crea el control. Si el control se especifica en una plantilla de cuadro de diálogo o si usa `CTreeView`, la creación es automática cuando se crea el cuadro de diálogo o la vista. Si desea crear el control de árbol como una ventana secundaria de alguna otra ventana, utilice la [crear](../mfc/reference/ctreectrl-class.md#create) función miembro.  
  
-   Si desea que el control de árbol para usar imágenes, establezca una lista de imágenes mediante una llamada a [SetImageList](../mfc/reference/ctreectrl-class.md#setimagelist). También puede cambiar la sangría llamando [SetIndent](../mfc/reference/ctreectrl-class.md#setindent). Es un buen momento para hacer esto en [OnInitDialog](../mfc/reference/cdialog-class.md#oninitdialog) (para los controles de cuadros de diálogo) o [OnInitialUpdate](../mfc/reference/cview-class.md#oninitialupdate) (para las vistas).  
  
-   Colocar datos en el control mediante una llamada a la `CTreeCtrl`del [InsertItem](../mfc/reference/ctreectrl-class.md#insertitem) función una vez para cada elemento de datos. `InsertItem`Devuelve un identificador para el elemento que se puede utilizar para hacer referencia a él más adelante, como cuando se agregan elementos secundarios. Es un buen momento para inicializar los datos en `OnInitDialog` (para los controles de cuadros de diálogo) o `OnInitialUpdate` (para las vistas).  
  
-   Cuando el usuario interactúa con el control, enviará varios mensajes de notificación. Puede especificar una función para controlar cada uno de los mensajes que desea controlar mediante la adición de un **ON_NOTIFY_REFLECT** macro en el mapa de mensajes de la ventana de control o mediante la adición de un `ON_NOTIFY` macro al mapa de mensajes de la ventana primaria. Vea [mensajes de notificación de controles de árbol](../mfc/tree-control-notification-messages.md) más adelante en este tema para obtener una lista de las notificaciones posibles.  
  
-   Llame a las distintas funciones de miembro Set para establecer valores para el control. Los cambios que puede realizar incluyen establecer la sangría y cambiar el texto, imágenes o datos asociados a un elemento.  
  
-   Utilizar las distintas funciones Get para examinar el contenido del control. También puede incluir el contenido del control de árbol con funciones que permiten recuperar identificadores de elementos primarios, secundarios y relacionados de un elemento especificado. Incluso puede ordenar a los elementos secundarios de un nodo determinado.  
  
-   Cuando haya terminado con el control, asegúrese de que se destruya correctamente. Si el control de árbol está en un cuadro de diálogo o si se trata de una vista y el `CTreeCtrl` automáticamente se destruirá el objeto. Si no es así, debe asegurarse de que tanto el control y la `CTreeCtrl` objeto se han destruido correctamente.  
  
## <a name="see-also"></a>Vea también  
 [Usar CTreeCtrl](../mfc/using-ctreectrl.md)   
 [Controles](../mfc/controls-mfc.md)

