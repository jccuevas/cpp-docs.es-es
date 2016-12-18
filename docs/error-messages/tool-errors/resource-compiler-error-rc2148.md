---
title: "Error del compilador de recursos RC2148 | Microsoft Docs"
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
  - "RC2148"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC2148"
ms.assetid: 0290065c-35d3-4815-80c5-40bf7132ae1d
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador de recursos RC2148
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el identificador de variante de idioma es demasiado grande  
  
 El valor del identificador de variante de idioma estaba fuera del intervalo.  
  
 La instrucción **LANGUAGE** debe usar la siguiente sintaxis:  
  
 **LANGUAGE** *Id\_idioma\_primario*, *Id\_idioma\_secundario*  
  
 Los identificadores de variante de idioma están definidos como constantes **SUBLANG\_** dentro del archivo WINNT.h.