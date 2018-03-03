---
title: "Cómo: mostrar información de comandos en la barra de estado | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- prompts [MFC]
- displaying command status [MFC]
- status bars [MFC], message area
- status bars [MFC], displaying command information
ms.assetid: de895cbe-61ee-46bf-9787-76b247527d6d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: da836f48592d97b3526c568eb9d9a830428f53a3
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-display-command-information-in-the-status-bar"></a>Cómo: Mostrar información de comandos en la barra de estado
Al ejecutar el Asistente para aplicaciones para crear el esqueleto de la aplicación, puede admitir una barra de herramientas y una barra de estado. Solo una opción en el Asistente para aplicaciones admite ambas opciones. Cuando hay una barra de estado, la aplicación proporciona automáticamente información útil cuando el usuario mueve el puntero sobre los elementos de los menús. La aplicación muestra automáticamente una cadena de mensaje en la barra de estado cuando se resalta el elemento de menú. Por ejemplo, cuando el usuario mueve el puntero sobre la **cortar** comando el **editar** menú, la barra de estado puede mostrar ", se corta la selección y lo coloca en el Portapapeles" en el área de mensajes de la barra de estado. El símbolo del sistema de ayuda al usuario a comprender el propósito del elemento de menú. Esto también funciona cuando el usuario hace clic en un botón de barra de herramientas.  
  
 Puede agregar a esta Ayuda de la barra de estado mediante la definición de cadenas de mensajes de los elementos de menú que agregan al programa. Para ello, proporcione las cadenas de mensajes al editar las propiedades del elemento de menú en el editor de menús. Las cadenas que defina se almacenan en el archivo de recursos de la aplicación; tienen los mismos identificadores que los comandos que se explican.  
  
 Agrega de forma predeterminada, el Asistente para aplicaciones `AFX_IDS_IDLEMESSAGE`, el identificador de un mensaje de "Listo" estándar, que se muestra cuando el programa está esperando si hay mensajes nuevos. Si especifica la opción de ayuda contextual en el Asistente para aplicaciones, el mensaje se cambia a "Para obtener ayuda, presione F1."  
  
## <a name="see-also"></a>Vea también  
 [Control y asignación de mensajes](../mfc/message-handling-and-mapping.md)

