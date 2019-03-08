---
title: Filtrar Mostrar información de comandos en la barra de estado
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: c93787b3799306d6008299e7c1be6e429bc4c2d9
ms.sourcegitcommit: c3093251193944840e3d0a068ecc30e6449624ba
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/04/2019
ms.locfileid: "57282323"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Filtrar Mostrar información de comandos en la barra de estado

Al ejecutar el Asistente para aplicaciones para crear el esqueleto de la aplicación, puede admitir una barra de herramientas y una barra de estado. Sólo una opción en el Asistente para la aplicación es compatible con ambos. Cuando hay una barra de estado, la aplicación proporciona comentarios útiles automáticamente cuando el usuario mueve el puntero sobre los elementos en los menús. La aplicación muestra automáticamente una cadena de mensaje en la barra de estado cuando se resalta el elemento de menú. Por ejemplo, cuando el usuario mueve el puntero sobre el **cortar** comando el **editar** menú, puede mostrar la barra de estado "Se corta la selección y lo coloca en el Portapapeles" en el área de mensajes de la barra de estado. El símbolo del sistema de ayuda al usuario a comprender el propósito del elemento de menú. Esto también funciona cuando el usuario hace clic en un botón de barra de herramientas.

Puede agregar a esta Ayuda de la barra de estado mediante la definición de cadenas de mensajes de elementos de menú que se agreguen al programa. Para ello, proporcione las cadenas de mensajes al editar las propiedades del elemento de menú en el editor de menús. Las cadenas que defina se almacenan en el archivo de recursos de la aplicación; tienen los mismos identificadores que los comandos que se explican.

De forma predeterminada, el Asistente para la aplicación agrega **AFX_IDS_IDLEMESSAGE**, el identificador de un mensaje de "Listo" estándar, que se muestra cuando el programa está esperando nuevos mensajes. Si especifica la opción de ayuda contextual en el Asistente para aplicaciones, el mensaje se cambia a "Para obtener ayuda, presione F1."

## <a name="see-also"></a>Vea también

[Control y asignación de mensajes](../mfc/message-handling-and-mapping.md)
