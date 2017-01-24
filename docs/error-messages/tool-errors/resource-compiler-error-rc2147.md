---
title: "Error del compilador de recursos RC2147 | Microsoft Docs"
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
  - "RC2147"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2147"
ms.assetid: 09974f06-1731-4e70-b373-f9218e0ee8d9
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador de recursos RC2147
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el identificador de variante de idioma no es un número  
  
 El valor del identificador de variante de idioma debe ser un número.  
  
 La instrucción **LANGUAGE** debe usar la siguiente sintaxis:  
  
 **LANGUAGE** *Id\_idioma\_primario*, *Id\_idioma\_secundario*  
  
 Los identificadores de variante de idioma están definidos como constantes **SUBLANG\_** dentro del archivo WINNT.h.