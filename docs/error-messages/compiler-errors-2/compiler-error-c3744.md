---
title: Error del compilador C3744 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3744
dev_langs: C++
helpviewer_keywords: C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
caps.latest.revision: "11"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: fd5c11e88960f2b4332a586d2fe982a8ea94fdbd
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c3744"></a>Error del compilador C3744
__unhook debe tener al menos 3 argumentos para eventos administrados  
  
 El [__unhook](../../cpp/unhook.md) función debe tomar tres parámetros al usarla en un programa que se compila con extensiones administradas para C++.  
  
 `__hook`y `__unhook` no son compatibles con la programación / CLR. Utilice los operadores += y -= en su lugar.  
  
 Solo es accesible mediante la opción del compilador obsoleta C3744 **/CLR: oldSyntax**.  
