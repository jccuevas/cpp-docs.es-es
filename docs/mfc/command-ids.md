---
title: Identificadores de comando | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: b651c734fbd7098705801aefcaa490293a4d661d
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="command-ids"></a>Identificadores de comando
Un comando queda descrito completamente por su identificador de comando (codificado en el **WM_COMMAND** mensaje). Este identificador se asigna al objeto de interfaz de usuario que genera el comando. Por lo general, se denominan identificadores para la funcionalidad del objeto de interfaz de usuario que están asignados.  
  
 Por ejemplo, un elemento Borrar todo en el menú Edición podría asignarse un identificador como **ID_EDIT_CLEAR_ALL**. La biblioteca de clases predefine algunos identificadores, especialmente para los comandos que el marco de trabajo, controle como **ID_EDIT_CLEAR_ALL** o `ID_FILE_OPEN`. Aprenderá a crear identificadores para otros comandos.  
  
 Al crear sus propios menús en Visual C++ editor de menús, es una buena idea para seguir la biblioteca de clases de la convención de nomenclatura tal y como se muestra en `ID_FILE_OPEN`. [Comandos estándar](../mfc/standard-commands.md) explica los comandos estándares definidos por la biblioteca de clases.  
  
## <a name="see-also"></a>Vea también  
 [Objetos de interfaz de usuario e identificadores de comando](../mfc/user-interface-objects-and-command-ids.md)

