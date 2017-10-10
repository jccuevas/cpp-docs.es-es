---
title: Error del compilador C2447 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2447
dev_langs:
- C++
helpviewer_keywords:
- C2447
ms.assetid: d1bd6e9a-ee42-4510-ae5e-6b0378f7b931
caps.latest.revision: 10
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 20f9e3259b355a40875bd9fc06f04fe2bb3147d0
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2447"></a>Error del compilador C2447
'{': falta el encabezado de función (¿lista formal de estilo anterior?)  
  
 El compilador encontró una llave de apertura inesperada en el ámbito global. En la mayoría de los casos, la causa está en un encabezado de función que tiene un formato incorrecto, una declaración mal colocada o carácter de punto y coma desubicado. Para resolver este problema, compruebe que la llave de apertura va detrás de un encabezado con formato correcto y no va precedida de una declaración o un carácter de punto y coma desubicado.  
  
 Este error también puede deberse a una lista de argumentos formales del lenguaje C de estilo anterior. Para resolver este problema, refactorice la lista de argumentos para que utilice un estilo moderno; es decir, que vaya entre paréntesis.  
  
 El ejemplo siguiente genera C2447:  
  
```  
// C2447.cpp  
int c;  
{}       // C2447  
```
