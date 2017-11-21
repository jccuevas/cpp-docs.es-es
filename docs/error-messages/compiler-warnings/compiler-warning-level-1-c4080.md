---
title: Compilador advertencia (nivel 1) C4080 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: C4080
dev_langs: C++
helpviewer_keywords: C4080
ms.assetid: 964fb3f4-b9fd-450b-aa23-35cece126172
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 187456a528df6613bdcb8d919b7cb069b81b7a67
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-1-c4080"></a>Advertencia del compilador (nivel 1) C4080
se esperaba un identificador para el nombre de segmento; se encontró 'símbolo'  
  
 El nombre del segmento en [#pragma alloc_text](../../preprocessor/alloc-text.md) debe ser una cadena o un identificador. El compilador omite el pragma si no se encuentra un identificador válido.  
  
 El ejemplo siguiente genera la advertencia C4080:  
  
```  
// C4080.cpp  
// compile with: /W1  
extern "C" void func(void);  
  
#pragma alloc_text()   // C4080  
  
// try this line to resolve the warning  
// #pragma alloc_text("mysection", func)  
  
int main() {  
}  
  
void func(void) {  
}  
```