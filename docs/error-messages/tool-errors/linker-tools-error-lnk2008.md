---
title: "Error de las herramientas del vinculador LNK2008 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK2008"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK2008"
ms.assetid: bbcd83c5-c8ae-439e-a033-63643a5bb373
caps.latest.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 11
---
# Error de las herramientas del vinculador LNK2008
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

El destino de la corrección no está alineado 'symbol\_name'  
  
 LINK encontró un destino de corrección en el archivo objeto que no estaba correctamente alineado.  
  
 Este error puede producirlo una alineación de sección personalizada \(por ejemplo, \#pragma [pack](../../preprocessor/pack.md)\), el modificador [align](../../cpp/align-cpp.md) o el uso de código de lenguaje de ensamblado que modifica la alineación de la sección.  
  
 Si su código no utiliza lo anterior, el error lo produce el compilador.