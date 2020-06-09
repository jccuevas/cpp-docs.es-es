---
title: Identificadores de comando
ms.date: 11/04/2016
helpviewer_keywords:
- command IDs, MFC
- command IDs
ms.assetid: e0171a2b-45b9-41fa-945d-ec2f7602ded0
ms.openlocfilehash: f7d675891904301b16aafe3acb2c294eede6d8d8
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84619039"
---
# <a name="command-ids"></a>Identificadores de comando

Un comando se describe totalmente mediante su identificador de comando por sí solo (codificado en el mensaje de **WM_COMMAND** ). Este identificador se asigna al objeto de interfaz de usuario que genera el comando. Normalmente, los identificadores se denominan para la funcionalidad del objeto de interfaz de usuario al que están asignados.

Por ejemplo, se puede asignar un identificador como **ID_EDIT_CLEAR_ALL**a un elemento borrar todo del menú edición. La biblioteca de clases predefine algunos identificadores, especialmente para los comandos que el marco de trabajo administra por sí mismo, como **ID_EDIT_CLEAR_ALL** o **ID_FILE_OPEN**. Creará otros identificadores de comandos.

Al crear sus propios menús en el editor de menús de Visual C++, se recomienda seguir la Convención de nomenclatura de la biblioteca de clases, tal como se muestra en **ID_FILE_OPEN**. [Comandos estándar](standard-commands.md) explica los comandos estándar definidos por la biblioteca de clases.

## <a name="see-also"></a>Consulte también

[Objetos de interfaz de usuario e identificadores de comando](user-interface-objects-and-command-ids.md)
