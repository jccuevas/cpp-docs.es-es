---
title: "Error del compilador C3862 | Microsoft Docs"
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
  - "C3862"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3862"
ms.assetid: ba547366-4189-4077-8c00-ab45e08a9533
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3862
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'función': no puede compilar una función no administrada con \/clr:pure o \/clr:safe  
  
 Una compilación con **\/clr:pure** o **\/clr:safe** creará una imagen de MSIL, una imagen sin código nativo \(no administrado\).  Por consiguiente, no puede utilizar la pragma `unmanaged` en una compilación **\/clr:pure** o **\/clr:safe** .  
  
 Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) y [managed, unmanaged](../../preprocessor/managed-unmanaged.md).  
  
## Ejemplo  
 El código siguiente genera el error C3862:  
  
```  
// C3862.cpp  
// compile with: /clr:pure /c  
#pragma unmanaged  
void f() {}   // C3862  
```