---
title: Error del compilador C2480 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2480
dev_langs:
- C++
helpviewer_keywords:
- C2480
ms.assetid: 1a58d1c2-971b-4084-96fa-f94aa51c02f1
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 06f6c536d5756a19e28df7060373512e3e883a41
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2480"></a>Error del compilador C2480
'identificador': 'thread' sólo es válido para los elementos de datos de extensión estática  
  
 No se puede utilizar la `thread` con una variable automática, el miembro de datos no estáticos, el parámetro de función, o en las declaraciones de función o definiciones de atributo.  
  
 Use la `thread` atributo para variables globales, miembros de datos estáticos y variables estáticas locales únicamente.  
  
 El ejemplo siguiente genera C2480:  
  
```  
// C2480.cpp  
// compile with: /c  
__declspec( thread ) void func();   // C2480  
__declspec( thread ) static int i;   // OK  
```
