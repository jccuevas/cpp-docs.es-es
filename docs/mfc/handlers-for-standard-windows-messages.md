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
ms.openlocfilehash: 190acd619224bdf22a5c8d35f541fa48b6664fe1
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625756"
---
# <a name="handlers-for-standard-windows-messages"></a>Controladores para mensajes estándar de Windows

Los controladores predeterminados para los mensajes estándar de Windows (**WM_**) están predefinidos en la clase `CWnd` . La biblioteca de clases basa los nombres de estos controladores en el nombre del mensaje. Por ejemplo, el controlador del mensaje de **WM_PAINT** se declara en `CWnd` como:

`afx_msg void OnPaint();`

La palabra clave **afx_msg** sugiere el efecto de la palabra clave **virtual** de C++ al distinguir los controladores de otras `CWnd` funciones miembro. Sin embargo, tenga en cuenta que estas funciones no son realmente virtuales; en su lugar, se implementan a través de mapas de mensajes. Los mapas de mensajes dependen únicamente de las macros de preprocesador estándar, no de las extensiones del lenguaje C++. La palabra clave **afx_msg** se resuelve en un espacio en blanco después del preprocesamiento.

Para reemplazar un controlador definido en una clase base, simplemente defina una función con el mismo prototipo en la clase derivada y para crear una entrada de mapa de mensajes para el controlador. El controlador "reemplaza" cualquier controlador del mismo nombre en cualquiera de las clases base de la clase.

En algunos casos, el controlador debe llamar al controlador invalidado en la clase base para que las clases base y Windows puedan operar en el mensaje. La llamada al controlador de clase base en la invalidación depende de las circunstancias. A veces, debe llamar primero al controlador de clase base y, a veces, al final. A veces, se llama al controlador de clase base condicionalmente, si decide no controlar el mensaje usted mismo. A veces, debe llamar al controlador de clase base y, a continuación, ejecutar condicionalmente su propio código de controlador, dependiendo del valor o el estado devuelto por el controlador de la clase base.

> [!CAUTION]
> No es seguro modificar los argumentos que se pasan a un controlador si desea pasarlos a un controlador de clase base. Por ejemplo, puede que se sienta tentado a modificar el argumento *nChar* del `OnChar` controlador (para convertir a mayúsculas, por ejemplo). Este comportamiento es bastante poco oscuro, pero si necesita lograr este efecto, utilice la `CWnd` función miembro `SendMessage` en su lugar.

Cómo se determina la manera adecuada de invalidar un mensaje determinado cuando el [Asistente para clases](reference/mfc-class-wizard.md) escribe el esqueleto de la función de controlador para un mensaje determinado (por `OnCreate` ejemplo, un controlador para **WM_CREATE**, se esboza en la forma de la función miembro invalidada recomendada). En el ejemplo siguiente se recomienda que el controlador llame primero al controlador de clase base y continúe solo en la condición de que no devuelva-1.

[!code-cpp[NVC_MFCMessageHandling#3](codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Por Convención, los nombres de estos controladores comienzan por el prefijo "ON". Algunos de estos controladores no toman ningún argumento, mientras que otros toman varios. Algunos también tienen un tipo de valor devuelto distinto de **void**. Los controladores predeterminados para todos los mensajes de **WM_** se documentan en la *referencia de MFC* como funciones miembro de clase `CWnd` cuyos nombres empiezan por "ON". Las declaraciones de función miembro en `CWnd` tienen el prefijo **afx_msg**.

## <a name="see-also"></a>Consulte también

[Declarar funciones del controlador de mensajes](declaring-message-handler-functions.md)
