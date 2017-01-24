---
title: "Advertencia de las herramientas del vinculador LNK4070 | Microsoft Docs"
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
  - "LNK4070"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK4070"
ms.assetid: f95f179a-fff9-427e-bd51-466b3934517f
caps.latest.revision: 8
caps.handback.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia de las herramientas del vinculador LNK4070
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

La directiva \/OUT:nombredearchivo de .EXP difiere del nombre de archivo de salida 'nombredearchivo'; se omite la directiva  
  
 El `filename` especificado en la instrucción [NAME](../../build/reference/name-c-cpp.md) o [LIBRARY](../../build/reference/library.md) al crear el archivo .exp difiere del `filename` de resultados que se supuso de forma predeterminada o se especificó con la opción [\/OUT](../../build/reference/out-output-file-name.md).  
  
 Esta advertencia aparecerá si se cambia el nombre de un archivo de salida en el entorno de desarrollo y donde el archivo .def del proyecto no se haya actualizado.  Actualice manualmente el archivo .def para corregir esta advertencia.  
  
 Un programa cliente que utilice la DLL resultante podría tener problemas.