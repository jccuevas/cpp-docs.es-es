---
title: Error del compilador C2507 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2507
dev_langs: C++
helpviewer_keywords: C2507
ms.assetid: f102aff5-de7d-4c3f-9cac-2ddf9ce02b14
caps.latest.revision: "9"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f520dee6ad9630dc338010311119ae9f41bbf86b
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="compiler-error-c2507"></a>Error del compilador C2507
'identificador': hay demasiados modificadores virtuales en la clase base  
  
 Una clase o estructura se declara como `virtual` más de una vez. Solo un `virtual` modificador puede aparecer por cada clase en una lista de clases base.  
  
 El ejemplo siguiente genera C2507:  
  
```  
// C2507.cpp  
// compile with: /c  
class A {};  
class B : virtual virtual public A {};   // C2507  
class C : virtual public A {};   // OK  
```