---
title: "Error irrecuperable C1037 | Microsoft Docs"
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
  - "C1037"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1037"
ms.assetid: 79103bca-ccfb-42e7-aef9-9b90c15b162f
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error irrecuperable C1037
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede abrir el archivo objeto nombreArchivo  
  
 El archivo objeto especificado por [\/Fo](../../build/reference/fo-object-file-name.md) no se puede abrir.  
  
### Posibles causas del error:  
  
1.  Nombre de archivo no válido.  
  
2.  Memoria insuficiente para abrir el archivo.  
  
3.  Otro proceso está usando el archivo.  
  
4.  Un archivo de solo lectura tiene el mismo nombre.  
  
 En Visual C\+\+ .NET \(versión 1300 del compilador\), hay un error que necesita que la configuración regional del usuario se establezca correctamente cuando el nombre de archivo \(o la ruta de acceso del directorio al nombre de archivo\) contiene caracteres MBCS. Establecer la configuración regional del sistema no es suficiente; debe establecerse la configuración regional del usuario para procesar caracteres MBCS.