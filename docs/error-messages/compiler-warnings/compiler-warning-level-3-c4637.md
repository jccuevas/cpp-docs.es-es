---
title: Compilador advertencia (nivel 3) C4637 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- C4637
dev_langs:
- C++
helpviewer_keywords:
- C4637
ms.assetid: 5fd347c1-2de9-408f-9136-1bf1ff273622
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 99291b82b0107237b139d778cac53c5ae153455e
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-warning-level-3-c4637"></a>Advertencia del compilador (nivel 3) C4637
Destino del comentario de documento XML: \<incluyen > etiqueta descartada.  reason  
  
 La sintaxis de un [ \<incluyen >](../../ide/include-visual-cpp.md) etiqueta no es correcta.  
  
 El ejemplo siguiente genera la advertencia C4637:  
  
```  
// C4637.cpp  
// compile with: /clr /doc /LD /W3  
using namespace System;  
  
/// Text for class MyClass.  
public ref class MyClass {   
public:  
   /// <include file="c:\davedata\jtest\xml_include.doc"/>  
   // Try the following line instead:  
   // /// <include file='xml_include.doc' path='MyDocs/MyMembers/*' />  
   void MyMethod() {  
   }  
};   // C4637  
```