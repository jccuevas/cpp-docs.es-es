---
title: Identificadores de comando | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e1e03f10199c1b582a1a8603a6ea6c93e1d55473
ms.sourcegitcommit: 060f381fe0807107ec26c18b46d3fcb859d8d2e7
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/25/2018
ms.locfileid: "36931237"
---
# <a name="command-ids"></a>Identificadores de comando
Un comando queda descrito completamente por su identificador de comando (codificado en el **WM_COMMAND** mensaje). Este identificador se asigna al objeto de interfaz de usuario que genera el comando. Por lo general, se denominan identificadores para la funcionalidad del objeto de interfaz de usuario que están asignados.  
  
 Por ejemplo, un elemento Borrar todo en el menú Edición podría asignarse un identificador como **ID_EDIT_CLEAR_ALL**. La biblioteca de clases predefine algunos identificadores, especialmente para los comandos que el marco de trabajo, controle como **ID_EDIT_CLEAR_ALL** o **ID_FILE_OPEN**. Aprenderá a crear identificadores para otros comandos.  
  
 Al crear sus propios menús en Visual C++ editor de menús, es una buena idea para seguir la biblioteca de clases de la convención de nomenclatura tal y como se muestra en **ID_FILE_OPEN**. [Comandos estándar](../mfc/standard-commands.md) explica los comandos estándares definidos por la biblioteca de clases.  
  
## <a name="see-also"></a>Vea también  
 [Objetos de interfaz de usuario e identificadores de comando](../mfc/user-interface-objects-and-command-ids.md)

