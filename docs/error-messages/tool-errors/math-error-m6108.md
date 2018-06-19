---
title: Error matemático M6108 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4dfeca48aa04ebfbc097649e5c25253166c50dad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33325856"
---
# <a name="math-error-m6108"></a>Error matemático M6108
raíz cuadrada  
  
 El operando de una operación de raíz cuadrada era negativo.  
  
 El programa termina con el código de salida 136.  
  
> [!NOTE]
>  El `sqrt` función en la biblioteca de tiempo de ejecución de C y la función intrínseca FORTRAN **SQRT** no generan este error. La C `sqrt` función comprueba el argumento antes de realizar la operación y devuelve un valor de error si el operando es negativo. El FORTRAN **SQRT** función genera el error DOMAIN [M6201](../../error-messages/tool-errors/math-error-m6201.md) en lugar de este error.