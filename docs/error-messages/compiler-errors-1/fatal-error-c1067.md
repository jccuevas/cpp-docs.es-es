---
title: "Error irrecuperable C1067 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1067"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1067"
ms.assetid: e2c94be6-4573-4571-aac9-73d657fe9f96
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error irrecuperable C1067
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

límite del compilador : se ha superado el límite de tamaño de 64 K de un registro de tipo  
  
 Este error podría deberse a la presencia de un símbolo con un nombre decorado con más de 247 caracteres.  Para resolverlo, acorte el nombre del símbolo.  
  
 Cuando el compilador genera información de depuración, emite registros de tipo para definir tipos encontrados en el código fuente.  Por ejemplo, los registros de tipo incluyen structs simples y listas de argumentos de funciones.  Algunos de estos registros de tipo pueden ser listas grandes.  
  
 Hay un límite de 64 K en el tamaño de cualquier registro de tipo.  Si se supera el límite de 64 K, se produce este error.  
  
 El error C1067 también se puede producir si hay muchos símbolos con nombres largos o si una clase, struct o una unión tiene demasiados miembros.