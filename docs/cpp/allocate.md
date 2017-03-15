---
title: "allocate | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "allocate"
  - "allocate_cpp"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "__declspec (palabra clave) [C++], asignar"
  - "allocate __declspec (palabra clave)"
ms.assetid: 67828b31-de60-4c0e-b0a6-ef3aab22641d
caps.latest.revision: 6
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 6
---
# allocate
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 El especificador de declaración **allocate** designa el segmento de datos en el que se asignará el elemento de datos.  
  
## Sintaxis  
  
```  
  
__declspec(allocate("  
segname  
")) declarator  
```  
  
## Comentarios  
 El nombre *segname* se debe declarar con una de las instrucciones pragma siguientes:  
  
-   [code\_seg](../preprocessor/code-seg.md)  
  
-   [const\_seg](../preprocessor/const-seg.md)  
  
-   [data\_seg](../preprocessor/data-seg.md)  
  
-   [init\_seg](../preprocessor/init-seg.md)  
  
-   [section](../preprocessor/section.md)  
  
## Ejemplo  
  
```  
// allocate.cpp  
#pragma section("mycode", read)  
__declspec(allocate("mycode"))  int i = 0;  
  
int main() {  
}  
```  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [\_\_declspec](../cpp/declspec.md)   
 [Palabras clave de C\+\+](../cpp/keywords-cpp.md)