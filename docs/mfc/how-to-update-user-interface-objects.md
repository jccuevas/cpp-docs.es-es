---
title: 'Cómo: Actualizar objetos de la interfaz de usuario'
ms.date: 11/04/2016
helpviewer_keywords:
- menus [MFC], updating as context changes
- user interface objects [MFC], updating
- user interface objects [MFC]
- update handlers [MFC]
- enabling UI elements [MFC]
- disabling menus [MFC]
- updating user-interface objects [MFC]
- disabling UI elements [MFC]
- commands [MFC], updating UI
- enabling menus [MFC]
ms.assetid: 82f09773-c978-427b-b321-05a6143b7369
ms.openlocfilehash: 2e16d912d0fb9ac195df80846d5bd740d86e30ec
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50566067"
---
# <a name="how-to-update-user-interface-objects"></a>Cómo: Actualizar objetos de la interfaz de usuario

Normalmente, los elementos de menú y los botones de barra de herramientas tienen más de un estado. Por ejemplo, un elemento de menú está deshabilitado (atenuado) si no está disponible en este contexto. Los elementos de menú también pueden ser activada o desactivada. También se puede deshabilitar un botón de barra de herramientas si no está disponible o se puede proteger.

Que actualiza el estado de estos elementos, programa cambian las condiciones de forma lógica, si un elemento de menú genera un comando que se controla mediante, por ejemplo, un documento, tiene sentido que el documento actualice el elemento de menú. Probablemente, el documento contiene la información en el que se basa la actualización.

Si un comando tiene varios objetos de interfaz de usuario (quizás un elemento de menú y un botón de barra de herramientas), ambos se enrutan a la misma función de controlador. Encapsula el código de actualización de la interfaz de usuario para todos los objetos de interfaz de usuario equivalente en un solo lugar.

El marco de trabajo proporciona una interfaz adecuada para actualizar automáticamente los objetos de interfaz de usuario. Puede elegir realizar la actualización de alguna otra manera, pero la interfaz proporcionada es eficaz y fácil de usar.

Los temas siguientes explican el uso de los controladores actualizados:

- [Cuando se llama a los controladores de actualización](../mfc/when-update-handlers-are-called.md)

- [El ON_UPDATE_COMMAND_UI (macro)](../mfc/on-update-command-ui-macro.md)

- [CCmdUI (clase)](../mfc/the-ccmdui-class.md)

## <a name="see-also"></a>Vea también

[Menús](../mfc/menus-mfc.md)

