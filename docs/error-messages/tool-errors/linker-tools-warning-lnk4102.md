---
title: Las herramientas del vinculador LNK4102 advertencia | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK4102
dev_langs:
- C++
helpviewer_keywords:
- LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9daaffc4ddfa9a869c2e60e2c05dc2b7e296d94b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46031871"
---
# <a name="linker-tools-warning-lnk4102"></a>Advertencia de las herramientas del vinculador LNK4102

exportación del destructor 'name' de eliminación imagen no se ejecute correctamente

El programa intentó exportar un destructor de eliminación. La eliminación resultante puede producirse a través de un límite de DLL que un proceso puede liberar memoria que no es el propietario. Asegúrese de que el símbolo dado no aparece en el archivo .def, y que el símbolo no aparece como un argumento de la **/importar** o **/EXPORT** opción en la línea de comandos del vinculador.

Si va a reconstruir la biblioteca de tiempo de ejecución de C, puede ignorar este mensaje.