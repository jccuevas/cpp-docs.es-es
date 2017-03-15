---
title: Definir un controlador de mensajes para un mensaje reflejado | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-cpp
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.defining.msg.msghandler
dev_langs:
- C++
helpviewer_keywords:
- messages, reflected
- message handling, reflected messages
ms.assetid: 5a403528-58c5-46e7-90d5-4a77f0ab9b9c
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
ms.sourcegitcommit: 040985df34f2613b4e4fae29498721aef15d50cb
ms.openlocfilehash: 0033c75d351aa201a0c18e81395d764b9d45761b
ms.lasthandoff: 02/24/2017

---
# <a name="defining-a-message-handler-for-a-reflected-message"></a>Definir un controlador de mensajes para un mensaje reflejado
Una vez haya creado una nueva clase de control MFC, puede definir controladores de mensajes para él. Controladores de mensajes reflejados permiten a la clase del control controlar sus propios mensajes antes de que el elemento primario recibe el mensaje. Puede utilizar MFC [CWnd:: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) función para enviar mensajes desde un control a una ventana primaria.  
  
 Con esta funcionalidad, por ejemplo, es posible crear un cuadro de lista que se vuelva a dibujarse en lugar de confiar en la ventana primaria que hacer es así (dibujado por el propietario). Para obtener más información sobre los mensajes reflejados, vea [controlar mensajes reflejados](../../mfc/handling-reflected-messages.md).  
  
 Para crear un [control ActiveX](../../mfc/activex-controls-on-the-internet.md) con la misma funcionalidad, debe crear un proyecto para el control ActiveX.  
  
> [!NOTE]
>  No se puede agregar un mensaje reflejado (OCM_*mensaje*) para un control ActiveX control mediante la ventana Propiedades, como se describe a continuación. Debe agregar manualmente estos mensajes.  
  
### <a name="to-define-a-message-handler-for-a-reflected-message-from-the-properties-window"></a>Para definir un controlador de mensajes para un mensaje reflejado desde la ventana Propiedades  
  
1.  Agregar un control, como una lista, un control rebar, una barra de herramientas o un control de árbol a un proyecto MFC.  
  
2.  En la vista de clases, haga clic en el nombre de la clase del control.  
  
3.  En el [ventana propiedades](/visualstudio/ide/reference/properties-window), el nombre de clase del control aparece en el **nombre de la clase** lista.  
  
4.  Haga clic en el **mensajes** botón para mostrar los mensajes de Windows disponibles para agregar al control.  
  
5.  Desplácese hacia abajo en la lista de mensajes en la ventana Propiedades hasta que vea el encabezado **reflejado**. Como alternativa, haga clic en el **categorías** botón y contraer la vista para ver el **reflejado** encabezado.  
  
6.  Seleccione el mensaje reflejado para el que desea definir un controlador. Mensajes reflejados se marcan con un signo igual (=).  
  
7.  Haga clic en la celda en la columna derecha en la ventana Propiedades para mostrar el nombre sugerido para el controlador como \<agregar >*HandlerName*. (Por ejemplo, el **= WM_CTLCOLOR** controlador de mensajes sugiere \<agregar >**CtlColor**).  
  
8.  Haga clic en el nombre sugerido para Aceptar. El controlador se agrega al proyecto.  
  
     Los nombres de controlador de mensaje que ha agregado aparecen en la columna derecha de la ventana de mensajes reflejados.  
  
9. Para editar o eliminar un controlador de mensajes, repita los pasos del 4 al 7. Haga clic en la celda que contiene el nombre del controlador para modificar o eliminar y haga clic en la tarea apropiada.  
  
## <a name="see-also"></a>Vea también  
 [Asignar mensajes a funciones](../../mfc/reference/mapping-messages-to-functions.md)   
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una Variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función Virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)

