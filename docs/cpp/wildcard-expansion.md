---
title: "Expansi&#243;n de caracteres comod&#237;n | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "_setargv"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "_setargv (función)"
  - "asterisco (comodín)"
  - "línea de comandos, procesar argumentos"
  - "línea de comandos, comodines"
  - "comodines de línea de comandos"
  - "signo de interrogación, carácter comodín"
ms.assetid: 1a543398-607b-4404-93d1-45d290bde638
caps.latest.revision: 9
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 9
---
# Expansi&#243;n de caracteres comod&#237;n
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

## Específicos de Microsoft  
 Puede utilizar caracteres comodín \(signo de interrogación \(?\) y asterisco \(\*\)\) para especificar los argumentos de nombre de archivo y ruta de acceso en la línea de comandos.  
  
 Los argumentos de la línea de comandos se administran mediante una rutina denominada **\_setargv** \(o **\_wsetargv** en el entorno de caracteres anchos\), que, de forma predeterminada, no expande los caracteres comodín en cadenas independientes en la matriz de cadenas `argv`.  Para obtener más información sobre cómo habilitar la extensión de caracteres comodín, consulte [Expandir argumentos de caracteres comodín](../c-language/expanding-wildcard-arguments.md).  
  
## FIN de Específicos de Microsoft  
  
## Vea también  
 [main: inicio de programa](../cpp/main-program-startup.md)