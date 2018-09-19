---
title: Asistente para controladores de eventos | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- vc.codewiz.eventhandler.overview
dev_langs:
- C++
helpviewer_keywords:
- Event Handler Wizard [C++]
ms.assetid: af8e1835-94b1-4d9a-b353-c519e011d3a1
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4c2ff441fc38d460e27039d7825753a2011dac3e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45702772"
---
# <a name="event-handler-wizard"></a>Asistente para controladores de eventos
Este asistente agrega un controlador de eventos para un control de cuadro de diálogo a la clase que elija. Si agrega un controlador de eventos desde la [ventana Propiedades](/visualstudio/ide/reference/properties-window), solo lo puede agregar a la clase que implementa el cuadro de diálogo. Vea [Adición de controladores de eventos para controles de cuadros de diálogo](../windows/adding-event-handlers-for-dialog-box-controls.md) para obtener más información.  
  
- **Nombre de comando**

   Identifica el control seleccionado, para el que se agrega el controlador de eventos. Este cuadro no está disponible.  
  
- **Tipo de mensaje**

   Muestra la lista de controladores de mensajes posibles actuales para el control seleccionado.  
  
- **Nombre del controlador de función**

   Muestra el nombre de la función que se agrega para controlar el evento. De forma predeterminada, el nombre se basa en el tipo de mensaje y el comando, precedido por "On". Por ejemplo, para el botón denominado `IDC_BUTTON1`, el tipo de mensaje `BN_CLICKED` muestra el nombre del controlador de función `OnBnClickedButton1`.  
  
- **Lista de clases**

   Muestra las clases disponibles a las que se puede agregar un controlador de eventos. La clase para el cuadro de diálogo seleccionado se muestra en color rojo.  
  
- **Descripción del controlador**

   Proporciona una descripción para el elemento seleccionado en el cuadro **Tipo de mensaje**. Este cuadro no está disponible.  
  
- **Agregar y editar**

   Agrega el controlador de mensajes al objeto o la clase seleccionada y, después, abre el editor de texto por la función nueva para que pueda agregar el código del controlador de notificación del control.  
  
- **Editar código**

   Abre el editor de texto por la función existente seleccionada para que pueda agregar o editar el código del controlador de notificación del control.  
  
## <a name="see-also"></a>Vea también  
 [Agregar un controlador de eventos](../ide/adding-an-event-handler-visual-cpp.md)