---
title: "Advertencia del compilador (nivel 4) C4431 | Microsoft Docs"
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
  - "C4431"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4431"
ms.assetid: 58434ab6-dd8d-427b-953a-602fb7453ae6
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4431
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

falta el especificador de tipo; se presupone int.Nota: C no admite default\-int  
  
 Este error puede producirse como resultado del trabajo de conformidad del compilador realizado para Visual C\+\+ 2005: Visual C\+\+ ya no crea identificadores sin tipo como int de forma predeterminada.  El tipo de un identificador debe especificarse de forma explícita.  
  
 De forma predeterminada, esta advertencia está desactivada.  Para obtener más información, vea [Advertencias del compilador desactivadas de forma predeterminada](../../preprocessor/compiler-warnings-that-are-off-by-default.md).  
  
## Ejemplo  
 El ejemplo siguiente genera el error C4431.  
  
```  
// C4431.c  
// compile with: /c /W4  
#pragma warning(default:4431)  
i;   // C4431  
int i;   // OK  
```