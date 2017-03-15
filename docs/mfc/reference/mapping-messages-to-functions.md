---
title: Asignar mensajes a funciones | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.mapping.msg.function
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [C++], adding message handlers
- message maps [C++], mapping messages to functions
ms.assetid: a7727a62-f638-4b20-b7f5-131f47200d6a
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: 4fafe461008e3545243d693e0d9e34acd57163e0
ms.openlocfilehash: 584cc8b1f59f94d88718add5c21046c487b8556f
ms.lasthandoff: 02/24/2017

---
# <a name="mapping-messages-to-functions"></a>Asignar mensajes a funciones
La ventana Propiedades permite enlazar controladores de mensajes (funciones miembro de clases de interfaz de usuario MFC) para los mensajes generados por los recursos de la aplicación. Usar [mapas de mensajes MFC](../../mfc/messages-and-commands-in-the-framework.md) para crear el enlace.  
  
 Cuando utiliza la vista de clases para crear una nueva clase derivada de una de las clases de framework, lo automáticamente coloca un completo y funcional archivos de clase en el encabezado (. h) e implementación (.cpp) que especifique.  
  
> [!NOTE]
>  Para agregar una nueva clase que no controle mensajes, cree la clase directamente en el editor de texto.  
  
### <a name="to-define-or-remove-a-message-handler-using-the-properties-window"></a>Para definir o quitar un controlador de mensajes mediante la ventana Propiedades  
  
1.  En la vista de clases, haga clic en la clase.  
  
2.  En la ventana Propiedades, haga clic en el **mensajes** botón.  
  
    > [!NOTE]
    >  El **mensajes** botón está disponible cuando se selecciona el nombre de clase en la vista de clases o al hacer clic dentro de la ventana de código fuente.  
  
     Si el proyecto tiene un controlador para un mensaje, el nombre del controlador aparece en la columna derecha junto al mensaje.  
  
3.  Si el mensaje no tiene ningún controlador, a continuación, haga clic en la celda en la columna derecha en la ventana Propiedades para mostrar el nombre sugerido para el controlador como \<agregar >*HandlerName*. (Por ejemplo, el `WM_TIMER` controlador de mensajes sugiere \<agregar >`OnTimer`).  
  
4.  Haga clic en el nombre sugerido para agregar código auxiliar para la función.  
  
5.  Para editar un controlador de mensajes, haga doble clic en el mensaje en la vista de clases y modifique el código en la ventana de código fuente.  
  
 Para quitar un controlador de mensajes, haga doble clic en el controlador en la columna derecha y seleccione \<eliminar >*HandlerName*. Código de la función está comentado.  
  
## <a name="see-also"></a>Vea también  
 [Controlador de mensajes MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una Variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función Virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Agregar controladores de eventos para controles de cuadro de diálogo](../../windows/adding-event-handlers-for-dialog-box-controls.md)   
 [Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)

