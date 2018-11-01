---
title: Advertencia de las herramientas del vinculador LNK4006
ms.date: 11/04/2016
f1_keywords:
- LNK4006
helpviewer_keywords:
- LNK4006
ms.assetid: 3a637d17-1676-4ea6-bd8b-290137d28d3b
ms.openlocfilehash: c81c93a6df8c7eef809f243e3dc56164ea548371
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50472233"
---
# <a name="linker-tools-warning-lnk4006"></a>Advertencia de las herramientas del vinculador LNK4006

símbolo ya definido en el objeto; segunda definición omitida

El `symbol` proporcionado, que se muestra en su forma representativa, se definió varias veces. Cuando se produce esta advertencia, `symbol` se agregarán dos veces, pero se utilizará sólo el primer formulario.

Puede obtener esta advertencia si se intenta combinar dos bibliotecas de importación en uno.

Si va a reconstruir la biblioteca de tiempo de ejecución de C, puede ignorar este mensaje.

### <a name="to-fix-by-using-the-following-possible-solutions"></a>Use las soluciones posibles siguientes para corregirlo

1. El determinado `symbol` puede ser una función empaquetada, creada al compilar con [/Gy](../../build/reference/gy-enable-function-level-linking.md). Este símbolo se incluyó en más de un archivo, pero se ha cambiado entre las compilaciones. Vuelva a compilar todos los archivos que incluyen el `symbol`.

1. El determinado `symbol` es posible que se han definido forma diferente en dos objetos miembro de diferentes bibliotecas.

1. Absoluta es posible que se han definido dos veces, con un valor diferente en cada definición.

1. Si se recibe el mensaje de error al combinar las bibliotecas, `symbol` ya existe en la biblioteca que se está agregando.