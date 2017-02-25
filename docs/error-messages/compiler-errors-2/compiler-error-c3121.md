---
title: "Error del compilador C3121 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3121"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3121"
ms.assetid: 1d3c7be4-d42d-4def-8d53-182c0c5cc237
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error del compilador C3121
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede cambiar el GUID para la clase 'nombre\_de\_clase'  
  
 Se intentó cambiar el id. de clase con [\_\_declspec\(uuid\)](../../cpp/uuid-cpp.md).  
  
 Por ejemplo, el código siguiente genera C3121:  
  
```  
// C3121.cpp  
[emitidl];  
[module(name="MyLibrary")];  
  
[coclass, uuid="00000000-0000-0000-0000-111111111111"]  
class __declspec(uuid("00000000-0000-0000-0000-111111111112")) A   // C3121  
{  
};  
int main()  
{  
}  
```