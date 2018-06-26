---
title: Controlar comandos en el documento | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 7a1e848827b46d40c1ec39f2af4788e6957932c5
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36929117"
---
# <a name="handling-commands-in-the-document"></a>Controlar comandos en el documento
La clase de documento también puede controlar ciertos comandos generados por elementos de menú, botones de barra de herramientas o las teclas de aceleración. De forma predeterminada, `CDocument` controla la operación de guardar y guardar como comandos en el menú archivo, usa la serialización. Otros comandos que afectan a los datos también pueden controlarse mediante las funciones miembro de su documento. Por ejemplo, en el programa Scribble, la clase `CScribDoc` proporciona un controlador para el comando editar borrar todo, lo que elimina todos los datos almacenados actualmente en el documento. Documentos pueden tener mapas de mensajes, pero a diferencia de las vistas, los documentos no pueden controlar mensajes de Windows estándares, solo **WM_COMMAND** mensajes o "comandos".  
  
## <a name="see-also"></a>Vea también  
 [Uso de documentos](../mfc/using-documents.md)

