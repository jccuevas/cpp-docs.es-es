---
title: 'Cómo: Mostrar información de comandos en la barra de estado'
ms.date: 11/04/2016
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
ms.openlocfilehash: bff5d5b20ecc9b20b7b1e8335cda34d582441425
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84622531"
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Cómo: Mostrar información de comandos en la barra de estado

Al ejecutar el Asistente para aplicaciones para crear el esqueleto de la aplicación, puede admitir una barra de herramientas y una barra de estado. Solo una opción en el Asistente para aplicaciones admite ambos. Cuando hay una barra de estado, la aplicación proporciona automáticamente información útil a medida que el usuario mueve el puntero sobre los elementos de los menús. La aplicación muestra automáticamente una cadena de mensaje en la barra de estado cuando se resalta el elemento de menú. Por ejemplo, cuando el usuario mueve el puntero sobre el comando **cortar** en el menú **edición** , la barra de estado puede mostrar "corta la selección y la coloca en el portapapeles" en el área de mensajes de la barra de estado. El aviso ayuda al usuario a entender el propósito del elemento de menú. Esto también funciona cuando el usuario hace clic en un botón de la barra de herramientas.

Puede Agregar a esta ayuda de la barra de estado definiendo las cadenas de mensajes para los elementos de menú que agregue al programa. Para ello, proporcione las cadenas de mensajes al editar las propiedades del elemento de menú en el editor de menús. Las cadenas que defina se almacenan en el archivo de recursos de la aplicación; tienen los mismos identificadores que los comandos que explican.

De forma predeterminada, el Asistente para aplicaciones agrega **AFX_IDS_IDLEMESSAGE**, el identificador de un mensaje "listo" estándar, que se muestra cuando el programa está esperando mensajes nuevos. Si especifica la opción de ayuda contextual en el Asistente para aplicaciones, el mensaje cambia a "para obtener ayuda, presione F1".

## <a name="see-also"></a>Consulte también

[Control y asignación de mensajes](message-handling-and-mapping.md)
