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
ms.openlocfilehash: 9a136caf3a1d22151cb9cfd48e1cd3f999ab51ec
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/14/2020
ms.locfileid: "81370500"
---
# <a name="handlers-for-standard-windows-messages"></a>Controladores para mensajes estándar de Windows

Los controladores predeterminados**WM_** para los mensajes estándar `CWnd`de Windows ( WM_ ) están predefinidos en la clase . La biblioteca de clases basa los nombres de estos controladores en el nombre del mensaje. Por ejemplo, el **WM_PAINT** controlador del mensaje `CWnd` WM_PAINT se declara como:

`afx_msg void OnPaint();`

La palabra clave **afx_msg** sugiere el efecto de la palabra clave `CWnd` **virtual** C++ distinguiendo los controladores de otras funciones miembro. Tenga en cuenta, sin embargo, que estas funciones no son realmente virtuales; en su lugar se implementan a través de mapas de mensajes. Los mapas de mensajes dependen únicamente de macros de preprocesador estándar, no de extensiones al lenguaje C++. La palabra clave **afx_msg** se resuelve en espacios en blanco después del preprocesamiento.

Para invalidar un controlador definido en una clase base, simplemente defina una función con el mismo prototipo en la clase derivada y para crear una entrada de mapa de mensajes para el controlador. El controlador "reemplaza" cualquier controlador con el mismo nombre en cualquiera de las clases base de la clase.

En algunos casos, el controlador debe llamar al controlador invalidado en la clase base para que las clases base y Windows puedan funcionar en el mensaje. El lugar donde se llama al controlador de clase base en la invalidación depende de las circunstancias. A veces debe llamar al controlador de clase base primero y a veces último. A veces se llama al controlador de clase base condicionalmente, si decide no controlar el mensaje usted mismo. A veces debe llamar al controlador de clase base y, a continuación, ejecutar condicionalmente su propio código de controlador, dependiendo del valor o estado devuelto por el controlador de clase base.

> [!CAUTION]
> No es seguro modificar los argumentos pasados a un controlador si tiene la intención de pasarlos a un controlador de clase base. Por ejemplo, puede tener la tentación `OnChar` de modificar el *nChar* argumento del controlador (para convertir a mayúsculas, por ejemplo). Este comportamiento es bastante oscuro, pero si necesita `CWnd` lograr `SendMessage` este efecto, utilice la función miembro en su lugar.

¿Cómo se determina la forma correcta de invalidar un mensaje determinado Cuando el [Asistente](reference/mfc-class-wizard.md) para `OnCreate` clases escribe el esqueleto de la función de controlador para un mensaje determinado , un controlador para **WM_CREATE**, por ejemplo, esboza en forma de la función miembro invalidada recomendada. En el ejemplo siguiente se recomienda que el controlador primero llame al controlador de clase base y proceda solo con la condición de que no devuelva -1.

[!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]

Por convención, los nombres de estos controladores comienzan con el prefijo "On." Algunos de estos controladores no toman ningún argumento, mientras que otros toman varios. Algunos también tienen un tipo de valor devuelto distinto de **void**. Los controladores predeterminados para todos los mensajes **de** WM_ `CWnd` se documentan en la referencia de *MFC* como funciones miembro de la clase cuyos nombres comienzan por "On." Las declaraciones de `CWnd` la función miembro en tienen el prefijo **afx_msg**.

## <a name="see-also"></a>Consulte también

[Declarar funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
