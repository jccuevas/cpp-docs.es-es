---
title: Error del compilador C2432 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: C2432
dev_langs: C++
helpviewer_keywords: C2432
ms.assetid: 0e3326e8-cab1-45a5-b48d-61edd33793e8
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: d89d894738978359fa0cedb9a9da6c4f9781c135
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="compiler-error-c2432"></a>Error del compilador C2432
referencia no válida a datos de 16 bits en 'identificador'  
  
 Un registro de 16 bits se usa como un índice o un registro de base. El compilador no es compatible con la que hacen referencia a datos de 16 bits. registros de 16 bits no se puede usar como registros de índice o base al compilar para el código de 32 bits.  
  
 El ejemplo siguiente genera C2432:  
  
```  
// C2432.cpp  
// processor: x86  
int main() {  
   _asm mov eax, DWORD PTR [bx]   // C2432  
}  
```