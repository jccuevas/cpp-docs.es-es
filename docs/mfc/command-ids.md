---
title: Identificadores de comando | Microsoft Docs
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
ms.openlocfilehash: 5087c271151793169cbf7350f78750044ccead0b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46446977"
---
# <a name="command-ids"></a>Identificadores de comando

Un comando se describe con detalle por su identificador de comando (codificados en el **WM_COMMAND** mensaje). Este identificador se asigna al objeto de interfaz de usuario que genera el comando. Normalmente, se denominan identificadores para la funcionalidad del objeto de interfaz de usuario que están asignados.

Por ejemplo, un elemento de borrar todo en el menú Edición podría asignarse un identificador como **ID_EDIT_CLEAR_ALL**. La biblioteca de clases predefine algunos identificadores, especialmente para los comandos que el marco de trabajo propia, controla como **ID_EDIT_CLEAR_ALL** o **ID_FILE_OPEN**. Va a crear otros identificadores de comando.

Al crear sus propios menús de Visual C++ editor de menús, es una buena idea a la biblioteca de clases de seguir la convención de nomenclatura como se muestra en **ID_FILE_OPEN**. [Comandos estándar](../mfc/standard-commands.md) explica los comandos estándares definidos por la biblioteca de clases.

## <a name="see-also"></a>Vea también

[Objetos de interfaz de usuario e identificadores de comando](../mfc/user-interface-objects-and-command-ids.md)

