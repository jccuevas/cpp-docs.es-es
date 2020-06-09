---
title: Controlar comandos en el documento
ms.date: 11/04/2016
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
ms.openlocfilehash: ed2ef635437408cacfd600d6cdba4b3731d575b4
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84625739"
---
# <a name="handling-commands-in-the-document"></a>Controlar comandos en el documento

La clase de documento también puede controlar ciertos comandos generados por los elementos de menú, los botones de barra de herramientas o las teclas de aceleración. De forma predeterminada, `CDocument` controla los comandos guardar y guardar como en el menú Archivo, mediante la serialización. Otros comandos que afectan a los datos también pueden ser administrados por funciones miembro del documento. Por ejemplo, en el programa Scribble, la clase `CScribDoc` proporciona un controlador para el comando Editar todo borrado, que elimina todos los datos almacenados actualmente en el documento. Los documentos pueden tener mapas de mensajes, pero a diferencia de las vistas, los documentos no pueden controlar los mensajes de Windows estándar, solo **WM_COMMAND** mensajes o "comandos".

## <a name="see-also"></a>Consulte también

[Usar documentos](using-documents.md)
