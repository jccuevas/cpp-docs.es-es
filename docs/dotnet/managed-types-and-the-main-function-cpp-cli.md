---
title: "Tipos administrados y la funci&#243;n main (C++/CLI) | Microsoft Docs"
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
  - "main (función), en aplicaciones administradas"
  - "código administrado, main() (función)"
ms.assetid: 9d0e9620-58c4-4dac-a0e1-ffeb95f80fa5
caps.latest.revision: 12
caps.handback.revision: 12
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Tipos administrados y la funci&#243;n main (C++/CLI)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Cuando se escribe una aplicación utilizando **\/clr**, los argumentos de la función **main\(\)** no pueden ser de un tipo administrado.  
  
 El siguiente ejemplo muestra una firma correcta:  
  
```  
// managed_types_and_main.cpp  
// compile with: /clr  
int main(int, char*[], char*[]) {}  
```  
  
## Vea también  
 [Tipos administrados](../dotnet/managed-types-cpp-cli.md)