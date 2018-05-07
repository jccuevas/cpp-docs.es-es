---
title: Las herramientas del vinculador LNK4102 advertencia | Documentos de Microsoft
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
ms.openlocfilehash: 16d13dcbc6d15efd7cf3a7ea0a310de4ab7b0c93
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="linker-tools-warning-lnk4102"></a>Advertencia de las herramientas del vinculador LNK4102
exportación de la eliminación de destructor 'nombre'; Puede que la imagen no se ejecute correctamente  
  
 El programa intentó exportar un destructor de eliminación. La eliminación resultante puede producirse a través de un límite DLL que un proceso puede liberar memoria que no le pertenece. Asegúrese de que el símbolo dado no aparece en el archivo .def y que el símbolo no aparece como un argumento de la **/importar** o **/exportación** opción en la línea de comandos del vinculador.  
  
 Si va a reconstruir la biblioteca de tiempo de ejecución de C, puede omitir este mensaje.