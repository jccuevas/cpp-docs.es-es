---
title: Invalidar el enrutamiento de comandos estándar
ms.date: 11/04/2016
helpviewer_keywords:
- MFC, command routing
- command routing [MFC], overriding
- command handling [MFC], routing commands
- overriding, standard command routing
ms.assetid: 872b698a-7432-40c4-9008-68721e8effa5
ms.openlocfilehash: 680b185f8d68a834862bc0fe14bf6e7984effd65
ms.sourcegitcommit: c21b05042debc97d14875e019ee9d698691ffc0b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 06/09/2020
ms.locfileid: "84617722"
---
# <a name="overriding-the-standard-command-routing"></a>Invalidar el enrutamiento de comandos estándar

En raras ocasiones, cuando debe implementar alguna variación del enrutamiento del marco estándar, puede invalidarlo. La idea es cambiar el enrutamiento en una o más clases invalidando `OnCmdMsg` en esas clases. Haga lo siguiente:

- En la clase que interrumpe el orden de pasar a un objeto no predeterminado.

- En el nuevo objeto no predeterminado o en el destino del comando, a su vez, puede pasar comandos a.

Si inserta un nuevo objeto en el enrutamiento, su clase debe ser una clase de destino de comando. En las versiones de reemplazo de `OnCmdMsg` , asegúrese de llamar a la versión que está reemplazando. Vea la función miembro [OnCmdMsg](reference/ccmdtarget-class.md#oncmdmsg) de clase `CCmdTarget` en la *referencia de MFC* y las versiones de estas clases como `CView` y `CDocument` en el código fuente proporcionado para obtener ejemplos.

## <a name="see-also"></a>Consulte también

[Cómo el marco llama a un controlador](how-the-framework-calls-a-handler.md)
