---
title: "Error de las herramientas del vinculador LNK1301 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1301"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1301"
ms.assetid: 760da428-7182-4b25-b20a-de90d4b9a9cd
caps.latest.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 6
---
# Error de las herramientas del vinculador LNK1301
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

LTCG módulos clr encontrados, incompatibles con \/LTCG:parámetro  
  
 Un módulo compilado con \/clr y \/GL se pasó al vinculador junto con uno de los parámetros de optimizaciones guiadas por perfiles \(PGO\) de \/LTCG.  
  
 Las optimizaciones guiadas por perfiles no son compatibles con los módulos \/clr.  
  
 Para obtener más información, vea:  
  
-   [\/GL \(Optimización de todo el programa\)](../../build/reference/gl-whole-program-optimization.md)  
  
-   [\/LTCG \(Generación de código en tiempo de enlace\)](../../build/reference/ltcg-link-time-code-generation.md)  
  
-   [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md)  
  
-   [Optimizaciones guiadas por perfiles](../../build/reference/profile-guided-optimizations.md)  
  
### Para corregir este error  
  
1.  No compile con \/clr ni vincule con uno de los parámetros PGO en \/LTCG.  
  
## Ejemplo  
 El código siguiente genera el error LNK1301:  
  
```  
// LNK1301.cpp  
// compile with: /clr /GL /link /LTCG:PGI LNK1301.obj  
// LNK1301 expected  
class MyClass {  
public:  
   int i;  
};  
```