---
title: Advertencia de las herramientas del vinculador LNK4006
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: d949ba259de8e131f6191e757119b4c42effc3d4
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80194322"
---
# <a name="linker-tools-warning-lnk4006"></a>Advertencia de las herramientas del vinculador LNK4006

símbolo ya definido en el objeto; segunda definición omitida

El `symbol` proporcionado, que se muestra en su forma representativa, se definió varias veces. Cuando se encuentra esta advertencia, se agregará `symbol` dos veces, pero solo se usará su primer formulario.

Puede obtener esta advertencia si intenta combinar dos bibliotecas de importación en una sola.

Si va a volver a generar la biblioteca en tiempo de ejecución de C, puede pasar por alto este mensaje.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Para corregir mediante las siguientes posibles soluciones

1. El `symbol` determinado puede ser una función empaquetada, creada mediante compilación con [/GY](../../build/reference/gy-enable-function-level-linking.md). Este símbolo se incluyó en más de un archivo, pero se cambió entre las compilaciones. Vuelva a compilar todos los archivos que incluyan el `symbol`.

1. Es posible que el `symbol` determinado se haya definido de forma diferente en dos objetos miembro en bibliotecas diferentes.

1. Una absoluta puede haberse definido dos veces, con un valor diferente en cada definición.

1. Si se recibe el mensaje de error al combinar bibliotecas, `symbol` ya existe en la biblioteca que se va a agregar a.
