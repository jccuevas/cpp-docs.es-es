---
title: Advertencia de las herramientas del vinculador LNK4102
ms.date: 11/04/2016
f1_keywords:
- LNK4102
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
ms.openlocfilehash: 0f9c8649988dd3056e98730ac4b02022a8c9dd51
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643097"
---
# <a name="linker-tools-warning-lnk4102"></a>Advertencia de las herramientas del vinculador LNK4102

exportación del destructor 'name' de eliminación imagen no se ejecute correctamente

El programa intentó exportar un destructor de eliminación. La eliminación resultante puede producirse a través de un límite de DLL que un proceso puede liberar memoria que no es el propietario. Asegúrese de que el símbolo dado no aparece en el archivo .def, y que el símbolo no aparece como un argumento de la **/importar** o **/EXPORT** opción en la línea de comandos del vinculador.

Si va a reconstruir la biblioteca de tiempo de ejecución de C, puede ignorar este mensaje.