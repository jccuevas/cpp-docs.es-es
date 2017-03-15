---
title: "Error de las herramientas del vinculador LNK1200 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "LNK1200"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1200"
ms.assetid: 55771145-915e-4006-ac6c-ac702041eb2f
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Error de las herramientas del vinculador LNK1200
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

error al leer base de datos del programa 'filename'  
  
 La base de datos de programa \(PDB\) no pudo leerse.  
  
 Este error puede estar motivado por los daños del archivo.  
  
 Si `filename` es la base de datos de programa \(PDB\) de un archivo objeto, vuelva a compilar el objeto con [\/Zi](../../build/reference/z7-zi-zi-debug-information-format.md).  
  
 Si `filename` es la base de datos de programa \(PDB\) del archivo de salida principal y este error se ha producido durante una vinculación incremental, elimine el archivo PDB y vuelva a vincular.