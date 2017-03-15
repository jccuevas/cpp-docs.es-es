---
title: "Advertencia de las herramientas del vinculador LNK4237 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4237"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4237"
ms.assetid: 87bfec39-5241-464f-9feb-517b49f352ea
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia de las herramientas del vinculador LNK4237
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Se especificó \/SUBSYSTEM:NATIVE al importar desde 'dll'; Utilice \/SUBSYSTEM:CONSOLE o \/SUBSYSTEM:WINDOWS.  
  
 [Se especificó \/SUBSYSTEM:NATIVE](../../build/reference/subsystem-specify-subsystem.md) al compilar una aplicación Windows \(Win32\) que utiliza directamente uno o varios de los siguientes archivos:  
  
-   kernel32.dll  
  
-   gdi32.dll  
  
-   user32.dll  
  
-   una de las DLL msvcrt\*.  
  
 Para resolver esta advertencia no especifique **\/SUBSYSTEM:NATIVE**.