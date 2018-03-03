---
title: Compilador advertencia (nivel 1) C4788 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C4788
dev_langs:
- C++
helpviewer_keywords:
- C4788
ms.assetid: 47d75bda-f833-4bdd-93a0-a134df0cd303
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e6f876dada851f46b7708ef1b34da4bae6f96dc0
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-1-c4788"></a>Advertencia del compilador (nivel 1) C4788
'identificador': el identificador se ha truncado a 'número' caracteres  
  
 El compilador limita la longitud máxima permitida para un nombre de función. Cuando el compilador genera funclets para código EH/SEH, crea el nombre del funclet anteponiendo algún texto en el nombre de función, por ejemplo, "__catch," "\__unwind", o en otra cadena.  
  
 El nombre del funclet resultante puede ser demasiado largo y el compilador lo truncará y generará la advertencia C4788.  
  
 Para resolver esta advertencia, acorte el nombre de función original. Si la función es un método o una función de plantilla de C++, utilice una definición de tipos para parte del nombre. Por ejemplo:  
  
```  
C1<x, y, z<T>>::C2<a,b,c>::f  
```  
  
 se puede reemplazar por:  
  
```  
typedef C1<x, y, z<T>>::C2<a,b,c> new_class ;  
new_class::f  
```  
  
 Esta advertencia solo aparece en el compilador de [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)].