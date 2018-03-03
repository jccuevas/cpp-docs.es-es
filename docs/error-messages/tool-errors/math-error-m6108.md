---
title: "Error matemático M6108 | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- M6108
dev_langs:
- C++
helpviewer_keywords:
- M6108
ms.assetid: 054893b4-49bc-45d9-882f-7cb50ba387c0
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: c6db123d9cb96274848a3edd9f845f86f413d8e0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="math-error-m6108"></a>Error matemático M6108
raíz cuadrada  
  
 El operando de una operación de raíz cuadrada era negativo.  
  
 El programa termina con el código de salida 136.  
  
> [!NOTE]
>  El `sqrt` función en la biblioteca de tiempo de ejecución de C y la función intrínseca FORTRAN **SQRT** no generan este error. La C `sqrt` función comprueba el argumento antes de realizar la operación y devuelve un valor de error si el operando es negativo. El FORTRAN **SQRT** función genera el error DOMAIN [M6201](../../error-messages/tool-errors/math-error-m6201.md) en lugar de este error.