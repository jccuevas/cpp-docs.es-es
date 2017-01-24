---
title: "Advertencia del compilador (nivel 3) C4622 | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-csharp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "C4622"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C4622"
ms.assetid: d3c879f0-4492-4f4b-b26d-230993f3a933
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Advertencia del compilador (nivel 3) C4622
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Reemplazando la información de depuración formada durante la creación del encabezado precompilado en el archivo objeto: 'file'  
  
 Se perdió la información de CodeView del archivo especificado al compilarse con la opción [\/Yu](../../build/reference/yu-use-precompiled-header-file.md) \(use encabezados precompilado.\).  
  
 Cambie el nombre del archivo objeto \(mediante [\/fo](../../build/reference/fo-object-file-name.md)\) al crear o usar el archivo de encabezado precompilado y vincúlelo con el nuevo archivo de objeto.