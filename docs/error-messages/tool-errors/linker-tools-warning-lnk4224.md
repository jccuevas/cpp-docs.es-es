---
title: "Advertencia de las herramientas del vinculador LNK4224 | Microsoft Docs"
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
  - "LNK4224"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4224"
ms.assetid: 8624b70e-0b93-43cf-b457-834d38632d0b
caps.latest.revision: 10
caps.handback.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4224
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

opción ya no se admite; se ha omitido  
  
 Se especificó una opción obsoleta y no válida del vinculador y se ha omitido.  
  
 Por ejemplo, LNK4224 puede aparecer si aparece una directiva \/comment en .obj.  La directiva \/comment se habría agregado a través del pragma [comentario](../../preprocessor/comment-c-cpp.md), utilizando la opción exestr obsoleta.  Utilice dumpbin [\/ALL](../../build/reference/all.md) para ver las directivas del vinculador en un archivo .obj.  
  
 Si es posible, modifique el origen para .obj y quite el pragma.  Si omite esta advertencia, es posible que un archivo ejecutable \(.executable\) compilado con **\/clr:pure** no se ejecute como se espera.  
  
## Ejemplo  
 El ejemplo siguiente genera el error LNK4224.  
  
```  
// LNK4224.cpp  
// compile with: /c /Zi  
// post-build command: link LNK4224.obj /debug /debugtype:map  
int main () {  
   return 0;  
}  
```