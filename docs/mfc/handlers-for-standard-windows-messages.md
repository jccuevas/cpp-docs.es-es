---
title: Controladores para mensajes estándar de Windows
ms.date: 11/04/2016
f1_keywords:
- afx_msg
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
ms.openlocfilehash: d60ae52225ddd993c1768d0b5ce1989ab0192e45
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57275394"
---
# <a name="handlers-for-standard-windows-messages"></a>Controladores para mensajes estándar de Windows

Predeterminada de controladores de mensajes estándares de Windows (**WM_**) están predefinidos en la clase `CWnd`. La biblioteca de clases base los nombres de estos controladores en el nombre del mensaje. Por ejemplo, el controlador para el **WM_PAINT** mensaje se declara en `CWnd` como:

`afx_msg void OnPaint();`

El **afx_msg** palabra clave sugiere el efecto de C++ **virtual** palabra clave y distingue los controladores de otras `CWnd` funciones miembro. Sin embargo, tenga en cuenta que estas funciones no son realmente virtuales; en su lugar se implementan a través de mapas de mensajes. Mapas de mensajes dependen exclusivamente estándares macros de preprocesador, no en las extensiones del lenguaje C++. El **afx_msg** palabra clave se resuelve en un espacio en blanco tras el preprocesamiento.

Para reemplazar un controlador definido en una clase base, simplemente defina una función con el mismo prototipo de la clase derivada y para crear una entrada de mapa de mensajes para el controlador. El controlador "reemplaza" cualquier controlador del mismo nombre en cualquiera de las clases de base de la clase.

En algunos casos, el controlador debe llamar al controlador de la clase base para que las clases base y Windows pueden operar en el mensaje. Donde llamar al controlador de la clase base en el reemplazo depende de las circunstancias. A veces, debe llamar primero a controlador de la clase base y último a veces. A veces llamar el controlador de clase base condicionalmente, si decide no controlar por sí mismo el mensaje. A veces, debe llamar al controlador de clase base, a continuación, ejecutar condicionalmente su propio código del controlador, según el valor o el estado devuelto por el controlador de clase base.

> [!CAUTION]
>  No es seguro modificar los argumentos pasados a un controlador si pretende pasarlos a un controlador de clase base. Por ejemplo, podría verse tentado a modificar el *nChar* argumento de la `OnChar` controlador (para convertir a mayúsculas, por ejemplo). Este comportamiento es muy poco claro, pero si necesita conseguir este efecto, utilice el `CWnd` función miembro `SendMessage` en su lugar.

¿Cómo se determina la manera adecuada para reemplazar un mensaje determinado cuando la ventana Propiedades crea el esqueleto de la función de controlador para un mensaje determinado, un `OnCreate` controlador para **WM_CREATE**, por ejemplo, esboza en forma de la función miembro reemplazado recomendada. En el ejemplo siguiente, se recomienda que el controlador primero llamar al controlador de clase base y continuar solo con condición de que no devuelve -1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Por convención, los nombres de estos controladores empiezan con el prefijo "On". Algunos de estos controladores no toman ningún argumento, mientras que otras toman varias. Algunos también tienen un tipo de valor devuelto distinto **void**. Los controladores predeterminados para todos los **WM_** se documentan los mensajes en el *referencia de MFC* como funciones miembro de clase `CWnd` cuyos nombres comienzan por "On". Las declaraciones de función miembro en `CWnd` tienen el prefijo **afx_msg**.

## <a name="see-also"></a>Vea también

[Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
