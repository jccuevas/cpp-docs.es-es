---
title: "Error de las herramientas del vinculador LNK1241 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1241"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1241"
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error de las herramientas del vinculador LNK1241
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ya se especificó el archivo de recursos 'archivo de recursos'  
  
 Este error se genera si se ejecuta **cvtres** manualmente desde la línea de comandos y, a continuación, se pasa el archivo .obj resultante al vinculador junto con los demás archivos .res.  
  
 Para especificar varios archivos .res, se deben pasar todos al compilador como archivos. res, no desde archivos .obj creados con **cvtres**.