---
title: Compilador advertencia (nivel 4) C4918 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4918
dev_langs:
- C++
helpviewer_keywords:
- C4918
ms.assetid: 1bcf6d35-3467-4aa8-b2ef-cb33f4e70238
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 317fd0bacb6e63ba7c10b4272a92c6d92710ac7e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-4-c4918"></a>Advertencia del compilador (nivel 4) C4918
'character': carácter no válido en la lista de optimizaciones de pragma  
  
 Se encontró un carácter desconocido en la lista de optimizaciones de una instrucción pragma [optimize](../../preprocessor/optimize.md) .  
  
 Por ejemplo, la siguiente instrucción genera la advertencia C4918:  
  
```  
// C4918.cpp  
// compile with: /W4  
#pragma optimize("X", on) // C4918 expected  
int main()  
{  
}  
```