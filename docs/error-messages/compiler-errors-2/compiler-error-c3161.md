---
title: C3161 de Error del compilador | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C3161
dev_langs: C++
helpviewer_keywords: C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4be981b2af166d85a3a83209a901f3e3e51b6246
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c3161"></a>C3161 de Error del compilador
'interfaz': anidamiento de una clase, estructura, unión o interfaz en una interfaz no es válido; anidamiento de una interfaz en una clase, struct o unión no es válido  
  
 Un [__interface](../../cpp/interface.md) solo puede aparecer en el ámbito global o dentro de un espacio de nombres. Una clase, struct o union no puede aparecer en una interfaz.  
  
## <a name="example"></a>Ejemplo  
 El ejemplo siguiente genera C3161.  
  
```  
// C3161.cpp  
// compile with: /c  
__interface X {  
   __interface Y {};   // C3161 A nested interface  
};  
```