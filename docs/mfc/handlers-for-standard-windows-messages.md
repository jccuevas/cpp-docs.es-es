---
title: Controladores para mensajes estándar de Windows | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
f1_keywords:
- afx_msg
dev_langs:
- C++
helpviewer_keywords:
- Windows messages [MFC], handlers
- message handling [MFC], Windows message handlers
- handler functions, standard Windows messages
- functions [MFC], handler
- messages [MFC], Windows
ms.assetid: 19412a8b-2c38-4502-81da-13c823c7e36c
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: d4ed4e022326d650b1012ad5244d8b18e9c789cc
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="handlers-for-standard-windows-messages"></a>Controladores para mensajes estándar de Windows
Predeterminado controladores para mensajes estándares de Windows (**WM_**) están predefinidas en la clase `CWnd`. La biblioteca de clases basará los nombres de estos controladores en el nombre del mensaje. Por ejemplo, el controlador para el `WM_PAINT` mensaje se declara en `CWnd` como:  
  
 `afx_msg void OnPaint();`  
  
 El **afx_msg** palabra clave sugiere el efecto de C++ **virtuales** palabra clave y distingue los controladores de otras `CWnd` funciones miembro. Sin embargo, tenga en cuenta que estas funciones no son realmente virtuales; en su lugar, se implementan a través de mapas de mensajes. Mapas de mensajes dependen exclusivamente de macros de preprocesador estándar, no en las extensiones del lenguaje C++. El **afx_msg** palabra clave se resuelve en un espacio en blanco tras el preprocesamiento.  
  
 Para reemplazar un controlador definido en una clase base, simplemente defina una función con el mismo prototipo en la clase derivada y para crear una entrada de mapa de mensajes para el controlador. El controlador "reemplaza" cualquier otro controlador del mismo nombre en cualquiera de las clases de base de la clase.  
  
 En algunos casos, el controlador debe llamar al controlador de la clase base para que la clase o clases base y las ventanas pueden operar en el mensaje. Donde se llamó a controlador de la clase base en la invalidación depende de las circunstancias. En ocasiones, debe llamar primero al controlador de clase base y a veces la última. En ocasiones se requieren el controlador de clase base condicionalmente, si decide no controlar el mensaje por sí mismo. A veces, debe llamar al controlador de clase base, a continuación, ejecutar condicionalmente su propio código del controlador, según el valor o estado devuelto por el controlador de clase base.  
  
> [!CAUTION]
>  No es seguro modificar los argumentos que se pasan a un controlador si pretende pasarlos a un controlador de clase base. Por ejemplo, es posible que vea tentado de modificar el `nChar` argumento de la `OnChar` controlador (para convertir a mayúsculas, por ejemplo). Este comportamiento es bastante oscuro, pero si necesita para lograr este efecto, utilice la `CWnd` función miembro **SendMessage** en su lugar.  
  
 ¿Cómo determina la manera adecuada para invalidar un mensaje determinado cuando la ventana Propiedades crea el esqueleto de la función de controlador para un mensaje determinado, un `OnCreate` controlador para `WM_CREATE`, por ejemplo, esboza en la forma de tal como se recomienda invalidar la función miembro. En el ejemplo siguiente, se recomienda que el controlador primero llamar al controlador de clase base y continuar solo a condición de que no devuelve -1.  
  
 [!code-cpp[NVC_MFCMessageHandling#3](../mfc/codesnippet/cpp/handlers-for-standard-windows-messages_1.cpp)]  
  
 Por convención, los nombres de estos controladores empiezan con el prefijo "On". Algunos de estos controladores no toman ningún argumento, mientras que otras usan varias. Algunas también tienen un tipo de valor devuelto distinto de `void`. Los controladores predeterminados para todos los **WM_** mensajes están documentados en la *referencia de MFC* como funciones miembro de clase `CWnd` cuyos nombres empiezan por "On". Las declaraciones de función de miembro en `CWnd` tienen el prefijo **afx_msg**.  
  
## <a name="see-also"></a>Vea también  
 [Declaración de funciones del controlador de mensajes](../mfc/declaring-message-handler-functions.md)
