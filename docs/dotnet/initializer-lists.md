---
title: "Listas de inicializadores | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "listas de inicializadores"
ms.assetid: b3e53442-9809-4105-9226-ae845bd20cae
caps.latest.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 4
---
# Listas de inicializadores
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Ahora se llama a las listas de inicializadores en los constructores antes que al constructor de la clase base.  
  
## Comentarios  
 Antes de Visual C\+\+ 2005, se llamaba al constructor de la clase base antes que a la lista de inicializadores al compilar con Extensiones administradas para C\+\+.  Ahora, al compilar con **\/clr**, se llama primero a la lista de inicializadores.  
  
## Vea también  
 [Cambio general en el lenguaje](../dotnet/general-language-changes-cpp-cli.md)