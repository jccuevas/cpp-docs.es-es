---
title: "Advertencia del compilador de recursos RC4005 | Microsoft Docs"
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
  - "RC4005"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC4005"
ms.assetid: 71f03b4a-c9a9-415d-920f-bf2e58507f93
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador de recursos RC4005
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

'identificador' : redefinición de macro  
  
 Se ha definido dos ves el identificador.  El compilador utilizó la segunda definición de macro.  
  
 Esta advertencia puede deberse a la definición de una macro en la línea de comandos y en el código con una directiva `#define`.  También se puede deber a macros importadas de archivos de inclusión.  
  
 Para eliminar la advertencia, se puede quitar una de las definiciones o usar una directiva `#undef` antes de la segunda definición.