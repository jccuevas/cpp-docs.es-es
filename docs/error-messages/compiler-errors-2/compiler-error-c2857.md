---
title: "Error del compilador C2857 | Microsoft Docs"
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
  - "C2857"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C2857"
ms.assetid: b57302bd-58ec-45ae-992a-1e282d5eeccc
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C2857
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

No se encontró la instrucción '\#include' especificada con la opción de la línea de comandos \/Ycfilename en el archivo de código fuente  
  
 La opción [\/Yc](../../build/reference/yc-create-precompiled-header-file.md) especifica el nombre de un archivo de inclusión que no está incluido en el archivo de código fuente compilado.  
  
 Una instrucción `#include` puede producir este error en un bloque de compilación condicional que no se compila.