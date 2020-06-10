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
ms.openlocfilehash: 43fb903fa169233ce532e41ecdf02c23ab6037c8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84621461"
---
# <a name="interpreting-user-input-through-a-view"></a>Interpretar la entrada del usuario a través de una vista

Otras funciones miembro de la vista controlan e interpretan todos los datos proporcionados por el usuario. Normalmente, se definen las funciones miembro de controlador de mensajes en la clase de vista para procesar:

- [Mensajes](messages.md) de Windows generados por acciones del mouse y del teclado.

- [Comandos](user-interface-objects-and-command-ids.md) de menús, botones de barra de herramientas y teclas de aceleración.

Estas funciones miembro de controlador de mensajes interpretan las siguientes acciones como entrada, selección o edición de datos, incluido el movimiento de datos hacia y desde el portapapeles:

- Movimientos y clics del mouse, arrastre y doble clic

- Pulsaciones

- Comandos de menú

Los mensajes de Windows que controla la vista dependen de las necesidades de la aplicación.

[Temas de control y asignación de mensajes](message-handling-and-mapping.md) explica cómo asignar elementos de menú y otros objetos de la interfaz de usuario a los comandos y cómo enlazar los comandos a las funciones de controlador. Los [temas de control y asignación de mensajes](message-handling-and-mapping.md) también explican el modo en que MFC enruta comandos y envía mensajes estándar de Windows a los objetos que contienen controladores para ellos.

Por ejemplo, es posible que la aplicación necesite implementar dibujo de mouse directo en la vista. El ejemplo Scribble muestra cómo controlar los mensajes WM_LBUTTONDOWN, WM_MOUSEMOVE y WM_LBUTTONUP respectivamente para comenzar, continuar y finalizar el dibujo de un segmento de línea. Por otro lado, en ocasiones es posible que necesite interpretar un clic del mouse en la vista como una selección. La función de controlador de la vista `OnLButtonDown` determinaría si el usuario estaba dibujando o seleccionando. Si selecciona, el controlador determinará si el clic estaba dentro de los límites de algún objeto en la vista y, en caso afirmativo, modifica la presentación para mostrar el objeto como seleccionado.

La vista también puede controlar determinados comandos de menú, como los del menú Editar para cortar, copiar, pegar o eliminar los datos seleccionados mediante el portapapeles. Este tipo de controlador llamaría a algunas de las funciones miembro relacionadas con el portapapeles de la clase `CWnd` para transferir un elemento de datos seleccionado a o desde el portapapeles.

## <a name="see-also"></a>Consulte también

[Usar vistas](using-views.md)
