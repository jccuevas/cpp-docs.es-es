---
title: Compilador advertencia (nivel 4) C4062 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C4062
dev_langs: C++
helpviewer_keywords: C4062
ms.assetid: 36d1c6ae-c917-4b08-bf30-2eb49ee94169
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 8e37e750ef3eabc3f48814e589113d4c63aa0dcb
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-warning-level-4-c4062"></a>Advertencia del compilador (nivel 4) C4062
el enumerador 'identificador' en una instrucción switch de la enumeración 'enumeración' no está controlado  
  
 La enumeración no tiene asociado ningún controlador en una instrucción `switch` y no hay ninguna etiqueta **predeterminada** .  
  
 De forma predeterminada, esta advertencia está desactivada. Vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md) para más información.  
  
 El siguiente ejemplo genera el error C4062:  
  
```  
// C4062.cpp  
// compile with: /W4  
#pragma warning(default : 4062)  
enum E { a, b, c };  
void func ( E e ) {  
   switch(e) {  
      case a:  
      case b:  
      break;   // no default label  
   }   // C4062, enumerate 'c' not handled  
}  
  
int main() {  
}  
```