---
title: Compilador advertencia (nivel 1) C4049 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4049
dev_langs:
- C++
helpviewer_keywords:
- C4049
ms.assetid: d11c1870-bcfc-4d71-8945-b87ec6ec3514
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 15d76be8cdf9855435094d02be5bc28fe27fe89a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4049"></a>Compilador advertencia (nivel 1) C4049
límite del compilador: finalizando la emisión de números de línea  
  
 El archivo contiene más de 16,777,215 (2<sup>24</sup>-1) líneas de código fuente. El compilador detiene la numeración en 16,777,215.  
  
 Para el código después de la línea 16,777,215:  
  
-   La imagen no contendrá ninguna información de depuración para los números de línea.  
  
-   Algunos diagnósticos pueden presentar con números de línea incorrectos.  
  
-   listas de ASM (/ FAs) pueden tener números de línea incorrectos.