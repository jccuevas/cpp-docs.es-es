---
title: "Error del compilador C2002 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C2002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2002"
ms.assetid: 91982314-203a-4de1-b884-94e39a623f61
caps.latest.revision: 10
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 10
---
# Error del compilador C2002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

constante de caracteres anchos no válida  
  
 La constante de caracteres multibyte no es válida.  
  
### Posibles causas del error:  
  
1.  La constante de caracteres anchos contiene más bytes de lo esperado.  
  
2.  No se ha incluido el encabezado estándar STDDEF.h.  
  
3.  Los caracteres anchos no se pueden concatenar con literales de cadena ordinarios.  
  
4.  Las constantes de caracteres anchos deben ir precedidas por un carácter 'L':  
  
    ```  
    L'mbconst'  
    ```  
  
5.  En Microsoft C\+\+, los argumentos de texto de una directiva de preprocesador deben ser ASCII.  Por ejemplo, la directiva `#pragma message(L"string")` no es válida.