---
title: "Especificar archivos DLL para carga retrasada | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DELAYLOAD (opción del vinculador)"
  - "carga retrasada de archivos DLL"
  - "carga retrasada de archivos DLL, especificar"
  - "DELAYLOAD (opción del vinculador)"
ms.assetid: 94cbecfe-7a42-40d1-a618-9f2786bac0d8
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Especificar archivos DLL para carga retrasada
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Puede especificar de qué archivos DLL retrasar la carga con la opción del vinculador [\/delayload](../../build/reference/delayload-delay-load-import.md):`dllname`.  Si no piensa usar su propia versión de una función auxiliar, también debe vincular el programa con delayimp.lib \(para aplicaciones de escritorio\) o dloadhelper.lib \(para aplicaciones de la tienda\).  
  
 El siguiente es un ejemplo sencillo de retraso de la carga de un archivo DLL:  
  
```  
// cl t.cpp user32.lib delayimp.lib  /link /DELAYLOAD:user32.dll  
#include <windows.h>  
// uncomment these lines to remove .libs from command line  
// #pragma comment(lib, "delayimp")  
// #pragma comment(lib, "user32")  
  
int main() {  
   // user32.dll will load at this point  
   MessageBox(NULL, "Hello", "Hello", MB_OK);  
}  
```  
  
 Genera la versión de depuración del proyecto.  Recorra el código usando el depurador y observará que el archivo user32.dll solo se carga cuando realiza la llamada a `MessageBox`.  
  
## Vea también  
 [Compatibilidad del vinculador con las DLL de carga retrasada](../../build/reference/linker-support-for-delay-loaded-dlls.md)