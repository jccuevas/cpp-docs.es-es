---
title: "Literales de cadena en expresiones primarias | Microsoft Docs"
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
  - "C"
helpviewer_keywords: 
  - "literales de cadena, en expresiones primarias"
ms.assetid: 3ec31278-527b-40d2-8c83-6b09e2d81ca6
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Literales de cadena en expresiones primarias
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Un “literal de cadena” es un carácter, un carácter ancho o una secuencia de caracteres consecutivos incluidos entre comillas dobles.  Puesto que no son variables, los literales de cadena ni ninguno de sus elementos pueden ser el operando izquierdo de una operación de asignación.  El tipo de un literal de cadena es una matriz de `char` \(o una matriz de `wchar_t` para literales de cadena anchos\).  Las matrices incluidas en expresiones se convierten en punteros.  Para obtener más información sobre las cadenas, vea [Literales de cadena](../c-language/c-string-literals.md).  
  
## Vea también  
 [Expresiones primarias de C](../c-language/c-primary-expressions.md)