---
title: Asistente para controladores de eventos | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-ide
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 3ccb80add8a98b9251a7ccbb5c85bf98b610a22e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="event-handler-wizard"></a>Asistente para controladores de eventos
Este asistente agrega un controlador de eventos para un control de cuadro de diálogo a la clase de su elección. Si agrega un controlador de eventos de la [ventana propiedades](/visualstudio/ide/reference/properties-window), puede agregarlo solamente a la clase que implementa el cuadro de diálogo. Vea [agregar controladores de eventos para controles de cuadros de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md) para obtener más información.  
  
 **Nombre de comando**  
 Identifica el control seleccionado, para el que se agrega el controlador de eventos. Este cuadro no está disponible.  
  
 **Tipo de mensaje**  
 Muestra la lista de controladores de mensajes posibles actual para el control seleccionado.  
  
 **Nombre del controlador de función**  
 Muestra el nombre de la función que se agrega para controlar el evento. De forma predeterminada, el nombre se basa en el tipo de mensaje y el comando, precedido por "On". Por ejemplo, para el botón denominado `IDC_BUTTON1`, el tipo de mensaje `BN_CLICKED` muestra el nombre del controlador de función `OnBnClickedButton1`.  
  
 **Lista de clases**  
 Muestra las clases disponibles que puede agregar un controlador de eventos. La clase para el cuadro de diálogo seleccionado se muestra en rojo.  
  
 **Descripción del controlador**  
 Proporciona una descripción para el elemento seleccionado en el **tipo de mensaje** cuadro. Este cuadro no está disponible.  
  
 **Agregar y editar**  
 Agrega el controlador de mensajes que el objeto o clase seleccionada y, a continuación, abre el editor de texto a la nueva función para que pueda agregar el código del controlador de notificación de control.  
  
 **Editar código**  
 Abre el editor de texto a la función existente seleccionada para que pueda agregar o editar el código del controlador de notificación de control.  
  
## <a name="see-also"></a>Vea también  
 [Agregar un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md)