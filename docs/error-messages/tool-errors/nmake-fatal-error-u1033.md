---
title: "Error grave de NMAKE U1033 | Microsoft Docs"
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
  - "U1033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "U1033"
ms.assetid: c146f7b5-7d5c-4329-a522-28a648546016
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error grave de NMAKE U1033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error de sintaxis : no se esperaba 'cadena'  
  
 La cadena no es parte de la sintaxis válida para un archivo MAKE.  
  
### Posibles causas del error:  
  
1.  Si el conjunto que cierre de corchetes angulares \(**\<\<**\) para un archivo en línea no está al principio de una línea, el error siguiente:  
  
    ```  
    syntax error : 'EOF' unexpected  
    ```  
  
2.  Si una definición de macro en el archivo MAKE contiene un signo igual \(**\=**\) sin un nombre delante o el nombre que se define es una macro que se expande a nada, se produce el siguiente error:  
  
    ```  
    syntax error : '=' unexpected  
    ```  
  
3.  Si el signo de punto y coma \(**;**\) de una línea de comentarios en TOOLS.INI no está al principio de la línea, se produce el siguiente error:  
  
    ```  
    syntax error : ';' unexpected  
    ```  
  
4.  Si el archivo MAKE recibe formato mediante un procesador de textos, se produce el siguiente error:  
  
    ```  
    syntax error : ':' unexpected  
    ```