---
title: Error matemático M6203 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- M6203
dev_langs:
- C++
helpviewer_keywords:
- M6203
ms.assetid: bd7fdd1c-83e4-4d6a-901e-10a0308bf5be
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 7660284f9e5e69b53f3289eaa1aa424944bbecb4
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33319317"
---
# <a name="math-error-m6203"></a>Error matemático M6203
'función': error _OVERFLOW  
  
 El resultado de la función especificada era demasiado grande para representarse.  
  
 Este error invoca la `_matherr` función con el nombre de función, sus argumentos y el tipo de error. Puede volver a escribir el `_matherr` función para personalizar el control de algunos errores matemáticos de punto flotante de tiempo de ejecución.