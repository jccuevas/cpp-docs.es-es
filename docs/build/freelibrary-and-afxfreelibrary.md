---
title: "FreeLibrary y AfxFreeLibrary | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "FreeLibrary"
  - "AfxFreeLibrary"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "archivos DLL de extensión [C++], descargar"
  - "AfxFreeLibrary (método)"
  - "descargar DLLs"
  - "FreeLibrary (método)"
  - "archivos DLL [C++], vincular"
  - "vinculación explícita [C++]"
  - "archivos DLL [C++], descargar"
ms.assetid: 4a48d290-3971-43e9-8e97-ba656cd0c8f8
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# FreeLibrary y AfxFreeLibrary
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Procesos que se vinculen explícitamente a un archivo DLL llaman a la función [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188) cuando el módulo del archivo DLL ya no se necesita.  Esta función reduce el número de referencias del módulo y, si dicho número es cero, elimina la asignación del espacio de direcciones del proceso.  
  
 En una aplicación MFC, utilice [AfxFreeLibrary](../Topic/AfxFreeLibrary.md) en lugar de `FreeLibrary` para descargar un archivo DLL de extensión.  La interfaz \(prototipo de función\) de `AfxFreeLibrary` es la misma que para `FreeLibrary`.  
  
## ¿Qué desea hacer?  
  
-   [Vincular de forma implícita](../build/linking-implicitly.md)  
  
-   [Determinar el método de vinculación que se va a utilizar](../build/determining-which-linking-method-to-use.md)  
  
## ¿Sobre qué desea obtener más información?  
  
-   [LoadLibrary y AfxLoadLibrary](../build/loadlibrary-and-afxloadlibrary.md)  
  
-   [GetProcAddress](../build/getprocaddress.md)  
  
## Vea también  
 [Archivos DLL en Visual C\+\+](../build/dlls-in-visual-cpp.md)   
 [FreeLibrary](http://go.microsoft.com/fwlink/p/?LinkID=259188)   
 [AfxFreeLibrary](../Topic/AfxFreeLibrary.md)