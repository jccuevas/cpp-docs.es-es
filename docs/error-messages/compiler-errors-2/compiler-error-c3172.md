---
title: "Error del compilador C3172 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C3172"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3172"
ms.assetid: 1834e2fd-6036-4c33-aff2-b51bc7c99441
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error del compilador C3172
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'nombre\_de\_módulo': no se pueden especificar distintos atributos idl\_module en un proyecto  
  
 Se encontraron atributos [idl\_module](../../windows/idl-module.md) con el mismo nombre pero distintos parámetros `dllname` o `version`en dos de los archivos de una compilación.  Sólo puede especificarse un único atributo `idl_module` por compilación.  
  
 Pueden especificarse atributos `idl_module` idénticos en más de un archivo de código fuente.  
  
 Por ejemplo, si se detectan los siguientes atributos `idl_module`:  
  
```  
// C3172.cpp  
[module(name="MyMod")];  
[ idl_module(name="x", dllname="file.dll", version="1.1") ];  
int main() {}  
```  
  
 Y, a continuación,  
  
```  
// C3172b.cpp  
// compile with: C3172.cpp  
// C3172 expected  
[ idl_module(name="x", dllname="file.dll", version="1.0") ];  
```  
  
 el compilador generará el error C3172 \(observe los diferentes valores de versión\).