---
title: "Advertencia de BSCMAKE BK4504 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "BK4504"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "BK4504"
ms.assetid: b56ee2d4-ad44-40f4-98c0-75934ea44a6c
caps.latest.revision: 8
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 8
---
# Advertencia de BSCMAKE BK4504
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

el archivo contiene demasiadas referencias; se omiten las demás referencias de este origen  
  
 El archivo .cpp contiene más de 64.000 referencias de símbolos.  Cuando BSCMAKE ha encontrado 64.000 referencias en un archivo, omite todos aún más las referencias.  
  
 Para corregir el problema, divide el archivo en dos o más archivos, que tiene menos de 64.000 referencias de símbolos, o utilizar la directiva de preprocesador de `#pragma component(browser)` para restringir los símbolos que se generan para las referencias específicas.  Para obtener más información, vea [component](../../preprocessor/component.md).