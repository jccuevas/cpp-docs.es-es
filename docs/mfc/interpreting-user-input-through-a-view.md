---
title: "Interpretar la entrada del usuario a través de una vista | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 263afe7b444722174d1787594f869087d606a235
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="interpreting-user-input-through-a-view"></a>Interpretar la entrada del usuario a través de una vista
Otras funciones miembro de la vista de manipular e interpretan todos los datos de usuario de entrada. Normalmente se definirán las funciones miembro de controlador de mensajes en la clase de vista para procesar:  
  
-   Windows [mensajes](../mfc/messages.md) generado por acciones del mouse y teclado.  
  
-   [Comandos](../mfc/user-interface-objects-and-command-ids.md) de menús, botones de barra de herramientas y teclas de aceleración.  
  
 Estas funciones miembro de controlador de mensajes a interpretar las siguientes acciones como entrada de datos, la selección o la edición, incluso mover datos hacia y desde el Portapapeles:  
  
-   Movimientos del mouse y los clics, arrastra y hace doble clic en  
  
-   Pulsaciones de teclas  
  
-   Comandos de menú  
  
 Los mensajes que Windows controle la vista depende de las necesidades de su aplicación.  
  
 [Temas de control y asignación de mensajes](../mfc/message-handling-and-mapping.md) explica cómo asignar elementos de menú y otros objetos de interfaz de usuario a los comandos y cómo enlazar los comandos a funciones del controlador. [Temas de control y asignación de mensajes](../mfc/message-handling-and-mapping.md) también explica cómo MFC enruta comandos y envía mensajes estándar de Windows a los objetos que contienen controladores para ellos.  
  
 Por ejemplo, la aplicación deba implementar directa mouse en la vista de dibujo. El ejemplo Scribble muestra cómo controlar la `WM_LBUTTONDOWN`, `WM_MOUSEMOVE`, y `WM_LBUTTONUP` mensajes respectivamente para comenzar, continuar y terminar el dibujo de un segmento de línea. Por otro lado, puede a veces es necesario interpretar un clic del mouse en la vista como una selección. La vista `OnLButtonDown` función de controlador debería determinar si el usuario se dibujando o seleccionar. Si seleccionar, el controlador debería determinar si el clic estaba dentro de los límites de un objeto en la vista y, si es así, modifique la presentación para mostrar el objeto como seleccionado.  
  
 La vista también podría controlar ciertos comandos de menú, tales como en el menú Edición para cortar, copiar, pegar o eliminar los datos seleccionados mediante el Portapapeles. Este tipo de controlador llamaría a algunos de los miembros relacionados con el Portapapeles las funciones de clase `CWnd` para transferir un elemento de datos seleccionado a o desde el Portapapeles.  
  
## <a name="see-also"></a>Vea también  
 [Uso de vistas](../mfc/using-views.md)

