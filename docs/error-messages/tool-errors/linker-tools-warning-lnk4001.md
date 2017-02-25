---
title: "Advertencia de las herramientas del vinculador LNK4001 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK4001"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4001"
ms.assetid: 0a8b1c3a-64ce-4311-b7c0-065995059246
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Advertencia de las herramientas del vinculador LNK4001
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

ningún archivo objeto especificado; bibliotecas usadas  
  
 Se han pasado al vinculador uno o más archivos .lib, pero ningún archivo .obj.  
  
 Debido a que el vinculador no puede tener acceso a información en un archivo .lib que sí tendría en un archivo .obj, esta advertencia indica que deberán especificarse explícitamente otras opciones del vinculador.  Por ejemplo, puede que haya que especificar las opciones [\/MACHINE](../../build/reference/machine-specify-target-platform.md), [\/OUT](../../build/reference/out-output-file-name.md), o [\/ENTRY](../../build/reference/entry-entry-point-symbol.md).