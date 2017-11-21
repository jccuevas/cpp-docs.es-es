---
title: Las herramientas del vinculador LNK4102 advertencia | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: LNK4102
dev_langs: C++
helpviewer_keywords: LNK4102
ms.assetid: bfd1b17e-05c7-4bc2-80d6-2888b1a425b2
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 0ac9cbdef0cc094888a2aba2098f1d655a351274
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="linker-tools-warning-lnk4102"></a>Advertencia de las herramientas del vinculador LNK4102
exportación de la eliminación de destructor 'nombre'; Puede que la imagen no se ejecute correctamente  
  
 El programa intentó exportar un destructor de eliminación. La eliminación resultante puede producirse a través de un límite DLL que un proceso puede liberar memoria que no le pertenece. Asegúrese de que el símbolo dado no aparece en el archivo .def y que el símbolo no aparece como un argumento de la **/importar** o **/exportación** opción en la línea de comandos del vinculador.  
  
 Si va a reconstruir la biblioteca de tiempo de ejecución de C, puede omitir este mensaje.