---
title: "Advertencia del compilador (nivel 1) C4096 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C4096"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4096"
ms.assetid: abf3cca2-2f21-45d8-b025-6b513b00681e
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4096
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'a': la interfaz no es del tipo COM; no se emitirá para IDL  
  
 Una definición de interfaz que puede haberse previsto como interfaz COM no se definió como interfaz COM y por lo tanto no se emitirá para el archivo IDL.  
  
 Vea [Atributos de interfaz](../../windows/interface-attributes.md) para ver una lista de los atributos que indican que una interfaz es una interfaz COM.  
  
 El código siguiente genera el error C4096:  
  
```  
// C4096.cpp  
// compile with: /W1 /LD  
#include "windows.h"  
[module(name="xx")];  
  
// [object, uuid("00000000-0000-0000-0000-000000000001")]  
__interface a  
{  
};  
  
[coclass, uuid("00000000-0000-0000-0000-000000000002")]  
struct b : a  
{  
};   // C4096, remove coclass or uncomment object  
```