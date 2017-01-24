---
title: "Error del compilador C3173 | Microsoft Docs"
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
  - "C3173"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C3173"
ms.assetid: edf79e10-e8cf-4f76-8d33-ab9d05e974e9
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error del compilador C3173
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

la versión no coincide en la combinación de IDL  
  
 Este error se produce cuando un archivo objeto contiene código IDL incrustado que se generó con una versión anterior del compilador.  El compilador codifica un número de versión para garantizar que el compilador usado para generar el contenido IDL que se incrusta en los archivos .obj sea el mismo que el utilizado para combinar el IDL incrustado.  
  
 Actualice su instalación de Visual C\+\+ para que todas las herramientas tengan la última versión.