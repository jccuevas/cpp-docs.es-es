---
title: "Error de las herramientas del vinculador LNK1561 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1561"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1561"
ms.assetid: cb0b709b-7c9c-4496-8a4e-9e1e4aefe447
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error de las herramientas del vinculador LNK1561
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se debe definir el punto de entrada  
  
 El vinculador no encontró un punto de entrada.  Puede que se haya previsto vincular como una DLL, en cuyo caso debería vincularse mediante la opción [\/DLL](../../build/reference/dll-build-a-dll.md).  También puede que se haya olvidado especificar el nombre del punto de entrada; vincule con la opción [\/ENTRY](../../build/reference/entry-entry-point-symbol.md).  
  
 En caso contrario, debería incluirse en el código una función main, wmain, WinMain, o wMain.  
  
 Si se utiliza [LIB](../../build/reference/lib-reference.md) y se intenta compilar un archivo .dll, una posible causa de este error es haber proporcionado un archivo .def.  Si es así, quite el archivo .def de la compilación.  
  
 El código siguiente genera el error LNK1561:  
  
```  
// LNK1561.cpp  
// LNK1561 expected  
int i;  
// add a main function to resolve this error  
```