---
title: "Advertencia del compilador (nivel 1) C4964 | Microsoft Docs"
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
  - "C4964"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4964"
ms.assetid: b89c9274-8a92-4b7c-aa30-3fbb1b68ac73
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 1) C4964
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se especificaron opciones de optimización; no se recopilará la información de perfil  
  
 Se especificaron [\/GL](../../build/reference/gl-whole-program-optimization.md) y [\/LTCG](../../build/reference/ltcg-link-time-code-generation.md) pero no se solicitaron optimizaciones, de manera que no se generarán archivos .pgc y, por tanto, no serán posibles las optimizaciones guiadas por perfiles.  
  
 Si desea generar archivos .pgc cuando ejecuta su aplicación, especifique una de las opciones [\/O](../../build/reference/o-options-optimize-code.md) del compilador.  
  
 El código siguiente genera el error C4964:  
  
```  
// C4964.cpp  
// compile with: /W1 /GL /link /ltcg:pgi  
// C4964 expected  
// Add /O2, for example, to the command line to resolve this warning.  
int main() {  
   int i;  
}  
```