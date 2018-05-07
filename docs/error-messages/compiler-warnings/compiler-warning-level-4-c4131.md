---
title: Compilador advertencia (nivel 4) C4131 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4131
dev_langs:
- C++
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6563d5faf3a9f050deb3cb7831c1a908739c8532
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="compiler-warning-level-4-c4131"></a>Advertencia del compilador (nivel 4) C4131
'función': usa un declarador de estilo anterior.  
  
 La declaración de función especificada no está en forma de prototipo.  
  
 Las declaraciones de función de estilo anterior deben convertirse a forma de prototipo.  
  
 En el ejemplo siguiente se muestra una declaración de función de estilo anterior:  
  
```  
// C4131.c  
// compile with: /W4 /c  
void addrec( name, id ) // C4131 expected  
char *name;  
int id;  
{ }  
```  
  
 En el ejemplo siguiente muestra una forma de prototipo:  
  
```  
void addrec( char *name, int id )  
{ }  
```