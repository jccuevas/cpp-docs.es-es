---
title: "Formato de im&#225;genes | Microsoft Docs"
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
ms.assetid: 3ca3654b-42fe-4253-9f2e-723644041aa0
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Formato de im&#225;genes
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

El formato de imágenes ejecutables es PE32\+.  Las imágenes ejecutables \(tanto DLL como EXE\) están restringidas a un tamaño máximo de 2 gigabytes, de modo que pueden utilizarse direcciones relativas con un desplazamiento de 32 bits para los datos de imágenes estáticas.  Estos datos incluyen la tabla de direcciones de importación, constantes de cadena, datos globales estáticos, etc.  
  
## Vea también  
 [Convenciones de software x64](../build/x64-software-conventions.md)