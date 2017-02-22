---
title: "Error de las herramientas del vinculador LNK1107 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1107"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1107"
ms.assetid: a37a893d-5efa-4eba-8f40-6c5518b4b9d0
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error de las herramientas del vinculador LNK1107
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

archivo no válido o dañado: no se puede leer en ubicación  
  
 La herramienta no pudo leer el archivo dado.  Vuelva a crear el archivo.  
  
 LNK1107 también se puede producir si intenta pasar un módulo \(extensión .dll o .netmodule creadas con [\/clr: noAssembly](../../build/reference/clr-common-language-runtime-compilation.md) o [\/NOASSEMBLY](../../build/reference/noassembly-create-a-msil-module.md)\) al vinculador; pase el archivo .obj en su lugar.  
  
 Si compila el siguiente ejemplo:  
  
```  
// LNK1107.cpp  
// compile with: /clr /LD  
public ref class MyClass {  
public:  
   void Test(){}  
};  
```  
  
 y, a continuación, especifique **link LNK1107.dll** en la línea de comandos, obtendrá LNK1107.  Para corregir este error, especifique **link LNK1107.obj**.