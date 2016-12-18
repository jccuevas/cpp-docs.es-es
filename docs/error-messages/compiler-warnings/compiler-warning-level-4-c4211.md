---
title: "Advertencia del compilador (nivel 4) C4211 | Microsoft Docs"
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
  - "C4211"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4211"
ms.assetid: 3eea3455-6faa-4cdb-8730-73db7026bd1f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 4) C4211
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

se ha utilizado una extensión no estándar: extern se ha vuelto a definir como static  
  
 Con las extensiones de Microsoft habilitadas \(\/Ze\), se puede redefinir un identificador `extern` como **static**.  
  
## Ejemplo  
  
```  
// C4211.c  
// compile with: /W4  
extern int i;  
static int i;   // C4211  
  
int main()  
{  
}  
```  
  
 Dichas redefiniciones no se permiten cuando se habilita la compatibilidad con ANSI \([\/Za](../../build/reference/za-ze-disable-language-extensions.md)\).  
  
## Vea también  
 [\(NOTINBUILD\)Static Storage\-Class Specifiers](http://msdn.microsoft.com/es-es/3ba9289a-a412-4a17-b319-ceb2c087df48)