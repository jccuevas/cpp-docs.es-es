---
title: Controlar comandos en el documento | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- message maps [MFC], in document class
- command handling [MFC]
- documents [MFC], message maps
- message handling [MFC], WM_COMMAND messages
- command handling [MFC], commands in documents
- documents [MFC], handling messages in
ms.assetid: c7375584-27af-4275-b2fd-afea476785d0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: a8d27698d573e1dee539f93ab88015285648fa77
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="handling-commands-in-the-document"></a>Controlar comandos en el documento
La clase de documento también puede controlar ciertos comandos generados por elementos de menú, botones de barra de herramientas o las teclas de aceleración. De forma predeterminada, **CDocument** controla la operación de guardar y guardar como comandos en el menú archivo, usa la serialización. Otros comandos que afectan a los datos también pueden controlarse mediante las funciones miembro de su documento. Por ejemplo, en el programa Scribble, la clase `CScribDoc` proporciona un controlador para el comando editar borrar todo, lo que elimina todos los datos almacenados actualmente en el documento. Documentos pueden tener mapas de mensajes, pero a diferencia de las vistas, los documentos no pueden controlar mensajes de Windows estándares, solo **WM_COMMAND** mensajes o "comandos".  
  
## <a name="see-also"></a>Vea también  
 [Uso de documentos](../mfc/using-documents.md)

