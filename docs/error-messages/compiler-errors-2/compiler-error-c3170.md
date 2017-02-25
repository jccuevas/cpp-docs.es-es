---
title: "Error del compilador C3170 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3170"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3170"
ms.assetid: ca9a59d6-7df3-42f0-b028-c09d0af3ac2a
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3170
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se pueden tener identificadores de módulo distintos en un proyecto  
  
 [Se encontraron atributos module](../../windows/module-cpp.md) con nombres diferentes en dos de los archivos de una compilación.  Sólo puede especificarse un atributo `module` único para cada compilación.  
  
 Pueden especificarse atributos `module` idénticos en más de un archivo de código fuente.  
  
 Por ejemplo, si se detectan los siguientes atributos de módulo:  
  
```  
// C3170.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
int main() {}  
```  
  
 Y, a continuación,  
  
```  
// C3170b.cpp  
// compile with: C3170.cpp  
// C3170 expected  
[ module(name="MyModule1", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f") ];  
```  
  
 el compilador generará el error C3170 \(observe los nombres diferentes\).