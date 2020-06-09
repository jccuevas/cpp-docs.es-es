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
ms.openlocfilehash: aec4067a7b5854ef872cfcef19a15db8438dd795
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84626387"
---
# <a name="how-to-update-user-interface-objects"></a>Cómo: Actualizar objetos de la interfaz de usuario

Normalmente, los elementos de menú y los botones de barra de herramientas tienen más de un estado. Por ejemplo, un elemento de menú está atenuado (atenuado) si no está disponible en el contexto actual. Los elementos de menú también se pueden activar o desactivar. También se puede deshabilitar un botón de la barra de herramientas si no está disponible o se puede comprobar.

Quién actualiza el estado de estos elementos a medida que las condiciones del programa cambian lógicamente, si un elemento de menú genera un comando controlado por, por ejemplo, un documento, tiene sentido que el documento actualice el elemento de menú. El documento probablemente contiene la información sobre la que se basa la actualización.

Si un comando tiene varios objetos de interfaz de usuario (quizás un elemento de menú y un botón de barra de herramientas), ambos se enrutan a la misma función de controlador. Esto encapsula el código de actualización de la interfaz de usuario para todos los objetos de interfaz de usuario equivalentes en un único lugar.

El marco de trabajo proporciona una interfaz adecuada para actualizar automáticamente los objetos de la interfaz de usuario. Puede optar por realizar la actualización de alguna otra forma, pero la interfaz proporcionada es eficaz y fácil de usar.

En los temas siguientes se explica el uso de controladores de actualización:

- [Cuando se llama a los controladores de actualización](when-update-handlers-are-called.md)

- [La macro ON_UPDATE_COMMAND_UI](on-update-command-ui-macro.md)

- [La clase CCmdUI](the-ccmdui-class.md)

## <a name="see-also"></a>Consulte también

[Menús](menus-mfc.md)
