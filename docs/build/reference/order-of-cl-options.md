---
title: Orden de las opciones de CL | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- cl
dev_langs:
- C++
helpviewer_keywords:
- cl.exe compiler, setting options
ms.assetid: 300908ce-ae00-4b45-964b-e4e69ff6777b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 165e20eefecd20ad9dec9e01b38c5eaa7926e4eb
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="order-of-cl-options"></a>Orden de las opciones de CL
Opciones pueden aparecer en cualquier parte en la línea de comandos de CL, excepto para la opción, que debe aparecer en último lugar. El compilador comienza con las opciones especificadas en el [variable de entorno de CL](../../build/reference/cl-environment-variables.md) y, a continuación, lee la línea de comandos de izquierda a derecha, procesando los archivos de comandos en el orden en los encuentra. Cada opción se aplica a todos los archivos en la línea de comandos. Si CL encuentra opciones en conflicto, utiliza la opción más a la derecha.  
  
## <a name="see-also"></a>Vea también  
 [Sintaxis de la línea de comandos del compilador](../../build/reference/compiler-command-line-syntax.md)