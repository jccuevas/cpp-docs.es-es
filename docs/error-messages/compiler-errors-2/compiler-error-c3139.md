---
title: "Error del compilador C3139 | Microsoft Docs"
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
  - "C3139"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3139"
ms.assetid: 95c92263-10ac-4ff3-b385-6312dd92adbc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3139
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'struct' : no se puede exportar un tipo definido por el usuario sin miembros  
  
 Se intentó aplicar el atributo [export](../../windows/export.md) a un tipo definido por el usuario vacío.  Por ejemplo:  
  
```  
// C3139.cpp  
#include "unknwn.h"  
[emitidl];  
[module(name=xx)];  
  
[export] struct MyStruct {   // C3139 empty type  
};  
int main(){}  
```