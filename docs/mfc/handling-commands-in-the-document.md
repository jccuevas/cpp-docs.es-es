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
ms.openlocfilehash: f3cce539d52bd04e97a6b5f84cbd833b05afb5bb
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62240579"
---
# <a name="handling-commands-in-the-document"></a>Controlar comandos en el documento

La clase de documento también puede controlar ciertos comandos generados por los elementos de menú, botones de barra de herramientas o las teclas de aceleración. De forma predeterminada, `CDocument` controla la operación de guardar y guardar como comandos en el menú archivo, utilizando la serialización. Otros comandos que afectan a los datos también pueden controlarse mediante las funciones miembro de su documento. Por ejemplo, en el programa Scribble, la clase `CScribDoc` proporciona un controlador para el comando editar borrar todo, lo que elimina todos los datos almacenados actualmente en el documento. Documentos pueden tener mapas de mensajes, pero a diferencia de las vistas, los documentos no pueden controlar mensajes de Windows estándar, solo **WM_COMMAND** mensajes o "commands".

## <a name="see-also"></a>Vea también

[Uso de documentos](../mfc/using-documents.md)
