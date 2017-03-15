---
title: "Advertencia de las herramientas del vinculador LNK4253 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4253"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4253"
ms.assetid: ec7433a9-aa9c-495a-a9f2-075e7bc3e7bc
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia de las herramientas del vinculador LNK4253
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

sección 'sección1' no combinada en 'sección2'; ya se combinó en 'sección3'  
  
 El vinculador detectó varias solicitudes de combinación contradictorias.  El vinculador omitirá una de las solicitudes.  
  
 Se encuentra una opción o directiva **\/MERGE** pero la sección `from` ya se ha combinado en una sección diferente debido a una opción o directiva **\/MERGE** previa \(o debido a una combinación implícita del vinculador\).  
  
 Para solucionarlo, quite una de las solicitudes de combinación.  
  
 Cuando Visual C\+\+ se destina a equipos x86 y Windows CE \(ARM, MIPS, SH4 y Thumb\), la sección .CRT es de solo lectura.  Si el código depende del comportamiento anterior \(las secciones .CRT son de lectura y escritura\), se podrían producir comportamientos inesperados.  
  
 Para obtener más información, vea  
  
-   [\/MERGE \(Combinar secciones\)](../../build/reference/merge-combine-sections.md)  
  
-   [comentario](../../preprocessor/comment-c-cpp.md)  
  
## Ejemplo  
 En el ejemplo siguiente, se indica al vinculador que combine dos veces la sección `.rdata`, pero en secciones diferentes.  El ejemplo siguiente genera el error LNK4253.  
  
```  
// LNK4253.cpp  
// compile with: /W1 /link /merge:.rdata=text2  
// LNK4253 expected  
#pragma comment(linker, "/merge:.rdata=.text")  
int main() {}  
```