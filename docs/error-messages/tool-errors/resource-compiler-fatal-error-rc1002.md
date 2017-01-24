---
title: "Error irrecuperable del compilador de recursos RC1002 | Microsoft Docs"
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
  - "RC1002"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1002"
ms.assetid: b43dfece-0dc3-4d0b-9d8f-509699b9ae80
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable del compilador de recursos RC1002
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

sin espacio en el montón  
  
### Se corrige mediante algunas de las siguientes posibles soluciones  
  
1.  Aumente el tamaño del archivo de intercambio de Windows.  Para obtener más información sobre cómo aumentar el tamaño del archivo de intercambio, busque memoria virtual en la Ayuda de Windows.  
  
2.  Divida el archivo actual en archivos más pequeños y compílelos por separado.  
  
3.  Quite otros programas o controladores que se estén ejecutando en el sistema.