---
title: "Comentarios en un archivo MAKE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "Make (archivos), comentarios"
ms.assetid: 76fd9e3d-5966-47f4-a091-c9e80b232b49
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Comentarios en un archivo MAKE
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Delante de un comentario se pone un signo de número \(\#\).  NMAKE omite el texto situado a partir del signo de número hasta el siguiente carácter de nueva línea.  Ejemplos:  
  
```  
# Comment on line by itself  
OPTIONS = /MAP  # Comment on macro definition line  
  
all.exe : one.obj two.obj  # Comment on dependency line  
    link one.obj two.obj  
# Comment in commands block  
#   copy *.obj \objects  # Command turned into comment  
    copy one.exe \release  
  
.obj.exe:  # Comment on inference rule line  
    link $<  
  
my.exe : my.obj ; link my.obj  # Err: cannot comment this  
 # Error: # must be the first character  
.obj.exe: ; link $<  # Error: cannot comment this  
```  
  
 Para especificar un signo de número literal, se ha de poner delante un símbolo de intercalación \(**^**\) del siguiente modo:  
  
```  
DEF = ^#define  #Macro for a C preprocessing directive  
```  
  
## Vea también  
 [Contenido de un archivo MAKE](../build/contents-of-a-makefile.md)