---
title: "Anotaciones de SAL | Microsoft Docs"
ms.custom: ""
ms.date: "12/14/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
  - "C"
helpviewer_keywords: 
  - "__bcount (anotación)"
  - "__checkreturn (anotación)"
  - "__deref (anotación)"
  - "__deref_opt (anotación)"
  - "__ecount (anotación)"
  - "__full (anotación)"
  - "__in (anotación)"
  - "__inout (anotación)"
  - "__nz (anotación)"
  - "__opt (anotación)"
  - "__out (anotación)"
  - "__part (anotación)"
  - "__ref (anotación)"
  - "__z (anotación)"
  - "_bcount (anotación)"
  - "_CA_SHOULD_CHECK_RETURN"
  - "_deref (anotación)"
  - "_deref_opt (anotación)"
  - "_ecount (anotación)"
  - "_full (anotación)"
  - "_in (anotación)"
  - "_inout (anotación)"
  - "_nz (anotación)"
  - "_opt (anotación)"
  - "_out (anotación)"
  - "_part (anotación)"
  - "_ref (anotación)"
  - "_z (anotación)"
  - "anotaciones [C++]"
  - "bcount (anotación)"
  - "deref (anotación)"
  - "deref_opt (anotación)"
  - "ecount (anotación)"
  - "full (anotación)"
  - "in (anotación)"
  - "inout (anotación)"
  - "nz (anotación)"
  - "opt (anotación)"
  - "out (anotación)"
  - "part (anotación)"
  - "ref (anotación)"
  - "anotaciones SAL"
  - "anotaciones SAL, _CA_SHOULD_CHECK_RETURN"
  - "z (anotación)"
ms.assetid: 81893638-010c-41a0-9cb3-666fe360f3e0
caps.latest.revision: 17
caps.handback.revision: 15
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Anotaciones de SAL
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Si examina los archivos de encabezado de la biblioteca, observará algunas anotaciones inusuales, como `_In_z` y `_Out_z_cap_(_Size)`.  Se trata de ejemplos del lenguaje de anotación de código fuente de Microsoft \(SAL\), que proporciona un conjunto de anotaciones para describir la forma en que una función usa sus parámetros; por ejemplo, las suposiciones que hace sobre ellos y lo que garantiza cuando finalice.  El archivo de encabezado \<sal.h\> define las anotaciones.  
  
 Para obtener más información sobre el uso de anotaciones SAL en [!INCLUDE[cpp_dev11_long](../build/includes/cpp_dev11_long_md.md)], vea [Utilizar anotaciones SAL para reducir defectos de código de C\/C\+\+](../Topic/Using%20SAL%20Annotations%20to%20Reduce%20C-C++%20Code%20Defects.md).  
  
## Vea también  
 [Características de la biblioteca CRT](../c-runtime-library/crt-library-features.md)