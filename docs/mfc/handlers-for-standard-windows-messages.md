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
ms.openlocfilehash: 4f512c3b9a7fce5cddd582fa774742d2b1ac0967
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907429"
---
# <a name="handlers-for-standard-windows-messages"></a>Controladores para mensajes estándar de Windows

Los controladores predeterminados para los mensajes estándar de Windows (**WM_** ) están `CWnd`predefinidos en la clase. La biblioteca de clases basa los nombres de estos controladores en el nombre del mensaje. Por ejemplo, el controlador del mensaje **WM_PAINT** se declara en `CWnd` como:

`afx_msg void OnPaint();`

La palabra clave **afx_msg** sugiere el efecto de C++ la palabra clave **virtual** mediante la distinción de los controladores `CWnd` de otras funciones miembro. Sin embargo, tenga en cuenta que estas funciones no son realmente virtuales; en su lugar, se implementan a través de mapas de mensajes. Los mapas de mensajes dependen únicamente de las macros de preprocesador estándar, no de las C++ extensiones del lenguaje. La palabra clave **afx_msg** se resuelve en el espacio en blanco después del preprocesamiento.

Para reemplazar un controlador definido en una clase base, simplemente defina una función con el mismo prototipo en la clase derivada y para crear una entrada de mapa de mensajes para el controlador. El controlador "reemplaza" cualquier controlador del mismo nombre en cualquiera de las clases base de la clase.

En algunos casos, el controlador debe llamar al controlador invalidado en la clase base para que las clases base y Windows puedan operar en el mensaje. La llamada al controlador de clase base en la invalidación depende de las circunstancias. A veces, debe llamar primero al controlador de clase base y, a veces, al final. A veces, se llama al controlador de clase base condicionalmente, si decide no controlar el mensaje usted mismo. A veces, debe llamar al controlador de clase base y, a continuación, ejecutar condicionalmente su propio código de controlador, dependiendo del valor o el estado devuelto por el controlador de la clase base.

> [!CAUTION]
>  No es seguro modificar los argumentos que se pasan a un controlador si desea pasarlos a un controlador de clase base. Por ejemplo, puede que se sienta tentado a modificar el argumento *nChar* del `OnChar` controlador (para convertir a mayúsculas, por ejemplo). Este comportamiento es bastante poco oscuro, pero si necesita lograr este efecto, utilice la `CWnd` función `SendMessage` miembro en su lugar.

Cómo se determina la manera adecuada de invalidar un mensaje determinado cuando el [Asistente para clases](reference/mfc-class-wizard.md) escribe el esqueleto de la función de controlador para un mensaje determinado `OnCreate` (un controlador para **WM_CREATE**, por ejemplo) se esboza en el formulario del recomendado función miembro invalidada. En el ejemplo siguiente se recomienda que el controlador llame primero al controlador de clase base y continúe solo en la condición de que no devuelva-1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Por Convención, los nombres de estos controladores comienzan por el prefijo "ON". Algunos de estos controladores no toman ningún argumento, mientras que otros toman varios. Algunos también tienen un tipo de valor devuelto distinto de **void**. Los controladores predeterminados para todos los mensajes **WM_** se documentan en la *referencia de MFC* como `CWnd` funciones miembro de clase cuyos nombres comienzan por "ON". Las declaraciones de función miembro en `CWnd` tienen el prefijo **afx_msg**.

## <a name="see-also"></a>Vea también

[Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
