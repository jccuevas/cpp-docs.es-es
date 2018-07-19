---
title: Compilador (nivel 1) la advertencia C4091 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4091
dev_langs:
- C++
helpviewer_keywords:
- C4091
ms.assetid: 3a404967-ab42-49b0-b324-fd7ba1859d78
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 79a0a74ad2cf6471679fd776f296d465ee8dd29c
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33276521"
---
# <a name="compiler-warning-level-1-c4091"></a>Compilador (nivel 1) la advertencia C4091
'keyword': omitido a la izquierda de 'tipo' cuando se declara ninguna variable  
  
 El compilador detectó una situación donde el usuario probablemente diseñado una variable que se declara, pero el compilador no pudo declarar la variable.  
  
## <a name="example"></a>Ejemplo  
 Un `__declspec` atributo al principio de una declaración de tipo definido por el usuario se aplica a la variable de ese tipo. C4091 indica que no hay ninguna variable se declara. El ejemplo siguiente genera la advertencia C4091.  
  
```  
// C4091.cpp  
// compile with: /W1 /c  
__declspec(dllimport) class X {}; // C4091  
  
// __declspec attribute applies to varX  
__declspec(dllimport) class X2 {} varX;  
  
// __declspec attribute after the class or struct keyword   
// applies to user defined type  
class __declspec(dllimport) X3 {};  
```  
  
## <a name="example"></a>Ejemplo  
 Si un identificador es una definición de tipo, no puede ser también un nombre de variable. El ejemplo siguiente genera la advertencia C4091.  
  
```  
// C4091_b.cpp  
// compile with: /c /W1 /WX  
#define LIST 4  
typedef struct _LIST {} LIST;   // C4091  
```