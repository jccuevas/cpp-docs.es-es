---
title: Interpretar la entrada del usuario a través de una vista
ms.date: 11/04/2016
helpviewer_keywords:
- interpreting user input through views [MFC]
- views [MFC], user interface and input
- input [MFC], view class [MFC]
- CView class [MFC], interpreting user input
- user input [MFC], interpreting through view class [MFC]
ms.assetid: f0302a70-661f-4781-8fe7-78f082bef2a5
ms.openlocfilehash: 3ef23ad74e1ff53d947453faa5682c5ecc1f4e43
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57304462"
---
# <a name="interpreting-user-input-through-a-view"></a>Interpretar la entrada del usuario a través de una vista

Otras funciones miembro de la vista de controlarán e interpretan todos los usuarios de entrada. Normalmente, definirá las funciones miembro de controlador de mensajes en la clase de vista para procesar:

- Windows [mensajes](../mfc/messages.md) generado por acciones del mouse y teclado.

- [Comandos](../mfc/user-interface-objects-and-command-ids.md) de menús, botones de barra de herramientas y teclas de aceleración.

Estas funciones miembro de controlador de mensajes a interpretar las siguientes acciones como entrada de datos, la selección o la edición, incluso mover datos hacia y desde el Portapapeles:

- Movimientos del mouse y clics, arrastra y hace doble clic en

- Pulsaciones de teclas

- Comandos de menú

Los mensajes que Windows controle la vista depende de las necesidades de su aplicación.

[Temas de control y asignación de mensajes](../mfc/message-handling-and-mapping.md) explica cómo asignar elementos de menú y otros objetos de interfaz de usuario a los comandos y cómo enlazar los comandos a las funciones de controlador. [Temas de control y asignación de mensajes](../mfc/message-handling-and-mapping.md) también se explica cómo MFC enruta los comandos y envía mensajes estándar de Windows a los objetos que contienen controladores para ellos.

Por ejemplo, la aplicación que tenga que implementar directo mouse en la vista de dibujo. El ejemplo Scribble muestra cómo controlar los mensajes WM_LBUTTONDOWN, WM_MOUSEMOVE y WM_LBUTTONUP respectivamente para comenzar, continuar y finalizar el dibujo de un segmento de línea. Por otro lado, es posible que a veces es necesario interpretar un clic del mouse en la vista como una selección. La vista `OnLButtonDown` función de controlador podría determinar si el usuario se dibujando o seleccionar. Si ha seleccionado, el controlador podría determinar si el clic estaba dentro de los límites de algún objeto en la vista y, si es así, cambiar la visualización para mostrar el objeto seleccionado.

La vista también podría controlar ciertos comandos de menú, tales como en el menú de edición para cortar, copiar, pegar o eliminar los datos seleccionados mediante el Portapapeles. Este tipo de controlador llamaría a algunos de los miembros relacionados con el Portapapeles funciones de la clase `CWnd` para transferir un elemento de datos seleccionado a o desde el Portapapeles.

## <a name="see-also"></a>Vea también

[Uso de vistas](../mfc/using-views.md)
