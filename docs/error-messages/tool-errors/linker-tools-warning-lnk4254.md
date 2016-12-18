---
title: "Advertencia de las herramientas del vinculador LNK4254 | Microsoft Docs"
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
  - "LNK4254"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4254"
ms.assetid: 6f41dfb3-ca21-40d3-bac7-b637e578efa4
caps.latest.revision: 9
caps.handback.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4254
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

sección 'sección1' \(desplazamiento\) combinada en 'sección2' \(desplazamiento\) con atributos diferentes  
  
 El contenido de una sección se combinó con otro, pero los atributos de las dos secciones son diferentes.  Su programa puede generar resultados inesperados.  Por ejemplo, los datos que deseaba que fuesen de sólo lectura, ahora pueden estar en una sección que permite la escritura.  
  
 Para resolver LNK4254, modifique o quite la solicitud de combinación.  
  
 Cuando Visual C\+\+ se destina a equipos x86 y Windows CE \(ARM, MIPS, SH4 y Thumb\), la sección .CRT es de solo lectura.  Si el código depende del comportamiento anterior \(las secciones .CRT son de lectura y escritura\), se podrían producir comportamientos inesperados.  
  
 Para obtener más información, vea  
  
-   [\/MERGE \(Combinar secciones\)](../../build/reference/merge-combine-sections.md)  
  
-   [comentario](../../preprocessor/comment-c-cpp.md)  
  
## Ejemplo  
 El ejemplo siguiente genera el error LNK4254.  
  
```  
// LNK4254.cpp  
// compile with: /W1 /link /WX  
// LNK4254 expected  
#pragma comment(linker, "/merge:.data=.text")  
int main() {}  
```