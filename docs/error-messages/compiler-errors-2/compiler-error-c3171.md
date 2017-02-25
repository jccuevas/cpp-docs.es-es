---
title: "Error del compilador C3171 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3171"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3171"
ms.assetid: 1ce26997-7ef1-4c9f-84da-003ea1a4251e
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error del compilador C3171
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'módulo': no se pueden especificar atributos module distintos en un proyecto  
  
 [Se encontraron atributos module](../../windows/module-cpp.md) con listas de parámetros diferentes en dos de los archivos de una compilación.  Sólo puede especificarse un atributo `module` único para cada compilación.  
  
 Pueden especificarse atributos `module` idénticos en más de un archivo de código fuente.  
  
 Por ejemplo, si se detectan los siguientes atributos `module`:  
  
```  
// C3171.cpp  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.0") ];  
int main() {}  
```  
  
 Y, a continuación,  
  
```  
// C3171b.cpp  
// compile with: C3171.cpp  
// C3171 expected  
[ module(name="MyModule", uuid="373a1a4e-469b-11d3-a6b0-00c04f79ae8f", version="1.1") ];  
```  
  
 el compilador generará el error C3171 \(observe los diferentes valores de versión\).