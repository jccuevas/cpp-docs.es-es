---
title: Error del compilador C3744 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: 11
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 87df3fd92ac3fcad9b3e87f02f16b8151e678b77
ms.contentlocale: es-es
ms.lasthandoff: 10/10/2017

---
# <a name="compiler-error-c3744"></a>Error del compilador C3744
__unhook debe tener al menos 3 argumentos para eventos administrados  
  
 El [__unhook](../../cpp/unhook.md) función debe tomar tres parámetros al usarla en un programa que se compila con extensiones administradas para C++.  
  
 `__hook`y `__unhook` no son compatibles con la programación / CLR. Utilice los operadores += y -= en su lugar.  
  
 Solo es accesible mediante la opción del compilador obsoleta C3744 **/CLR: oldSyntax**.  

