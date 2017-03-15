---
title: "Operador de conversi&#243;n a caracteres (#@) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "#@"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "#@ (operador de preprocesador)"
  - "operador de caracterización"
  - "preprocesador, operadores"
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Operador de conversi&#243;n a caracteres (#@)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

**Específicos de Microsoft**  
  
 El operador charizing solo puede utilizarse con argumentos de macros.  Si **\#@** precede a un parámetro formal en la definición de la macro, el argumento real se agrega entre comillas simples y se interpreta como un carácter cuando se expande la macro.  Por ejemplo:  
  
```  
#define makechar(x)  #@x  
```  
  
 hace que la instrucción  
  
```  
a = makechar(b);  
```  
  
 se expanda a  
  
```  
a = 'b';  
```  
  
 El carácter de comilla simple no se puede utilizar con el operador charizing.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Operadores de preprocesador](../preprocessor/preprocessor-operators.md)