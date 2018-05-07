---
title: Error del compilador C3744 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f96b8445c343bdd4f606157e692c4d6ce262e369
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-error-c3744"></a>Error del compilador C3744
__unhook debe tener al menos 3 argumentos para eventos administrados  
  
 El [__unhook](../../cpp/unhook.md) función debe tomar tres parámetros al usarla en un programa que se compila con extensiones administradas para C++.  
  
 `__hook` y `__unhook` no son compatibles con la programación / CLR. Utilice los operadores += y -= en su lugar.  
  
 Solo es accesible mediante la opción del compilador obsoleta C3744 **/CLR: oldSyntax**.  
