---
title: "Error en tiempo de ejecuci&#243;n de C R6030 | Microsoft Docs"
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
  - "R6030"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "R6030"
ms.assetid: 0238a6c3-a033-4046-8adc-f8f99d961153
caps.latest.revision: 9
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error en tiempo de ejecuci&#243;n de C R6030
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

CRT no inicializado  
  
 Este error se produce si utiliza CRT, pero no se ha ejecutado el código de inicio de CRT.  Puede aparecer este error si se utiliza el modificador de vinculador [\/ENTRY](../../build/reference/entry-entry-point-symbol.md) para reemplazar la dirección inicial predeterminada, generalmente **mainCRTStartup**, **wmainCRTStartup** para un archivo EXE de la consola, **WinMainCRTStartup** o **wWinMainCRTStartup** para un archivo EXE de Windows o **\_DllMainCRTStartup** para un archivo DLL.  Si no se llama a una de las funciones anteriores en el inicio, no se inicializará la biblioteca en tiempo de ejecución de C.