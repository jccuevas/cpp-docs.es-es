---
title: "Vinculaci&#243;n en nombres con &#225;mbito de clase | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "nombres de clase [C++], vinculación"
  - "ámbito de clase [C++], vinculación en nombres con"
  - "clases [C++], nombres"
  - "clases [C++], ámbito"
  - "vinculación externa, reglas de vinculación de ámbito"
  - "vinculación [C++], reglas de vinculación de ámbito"
  - "nombres [C++], reglas de vinculación de ámbito"
  - "ámbito [C++], nombres de clase"
  - "ámbito [C++], reglas de vinculación"
ms.assetid: 45275ff3-6e94-4967-82c8-ba540ef4da28
caps.latest.revision: 8
caps.handback.revision: 8
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Vinculaci&#243;n en nombres con &#225;mbito de clase
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Las siguientes reglas de vinculación se aplican a los nombres con ámbito de clase:  
  
-   Los miembros de clases estáticas tienen vinculación externa.  
  
-   Las funciones de miembro de clase tienen vinculación externa.  
  
-   Los enumeradores y los nombres `typedef` no tienen ninguna vinculación.  
  
 **Específicos de Microsoft**  
  
-   Las funciones declaradas como funciones `friend` deben tener vinculación externa.  Si se declara una función estática como `friend` se produce un error.  
  
 **FIN de Específicos de Microsoft**  
  
## Vea también  
 [Programa y vinculación](../cpp/program-and-linkage-cpp.md)