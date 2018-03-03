---
title: Error del compilador C2523 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2523
dev_langs:
- C++
helpviewer_keywords:
- C2523
ms.assetid: 7951b700-8f37-45a0-beb4-a79ae0ced72e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 9fbfb9a2302f306401ad6c824fda17303e47f5bb
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2523"></a>Error del compilador C2523
' clase:: ~ identificador ': error de coincidencia de etiqueta de destructor/finalizador  
  
 El nombre del destructor debe ser el nombre de clase precedido por una tilde (`~`). El constructor y el destructor son los únicos miembros que tienen el mismo nombre que la clase.  
  
 El ejemplo siguiente genera C2523:  
  
```  
// C2523.cpp  
// compile with: /c  
class A {  
   ~B();    // C2523  
   ~A();   // OK  
};  
```