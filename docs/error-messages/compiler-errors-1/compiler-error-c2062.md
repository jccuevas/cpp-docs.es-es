---
title: Error de compilador Error C2062 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
caps.latest.revision: 9
author: corob-msft
ms.author: corob
manager: ghogen
ms.translationtype: MT
ms.sourcegitcommit: 35b46e23aeb5f4dbfd2a0dd44b906389dd5bfc88
ms.openlocfilehash: 775923345052aba99b05f708c417b8bed267119b
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="compiler-error-c2062"></a>Error de compilador Error C2062
tipo 'type' inesperado  
  
 El compilador no esperaba un nombre de tipo.  
  
 El ejemplo siguiente genera el error C2062:  
  
```  
// C2062.cpp  
// compile with: /c  
struct A {  : int l; };   // C2062  
struct B { private: int l; };   // OK  
```  
  
 Error C2062 también puede producirse debido a la manera en que el compilador controla los tipos indefinidos en la lista de parámetros del constructor. Si el compilador encuentra un tipo indefinido (o mal escrito), supone que el constructor es una expresión y emite el error C2062. Para resolverlo, utilice sólo tipos definidos en una lista de parámetros de constructor.
