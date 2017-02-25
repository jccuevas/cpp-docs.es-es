---
title: "Error irrecuperable C1033 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "C1033"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "C1033"
ms.assetid: 09976c03-8450-4cf7-8b43-1b91c2c2b9f9
caps.latest.revision: 9
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 9
---
# Error irrecuperable C1033
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

no se puede abrir la base de datos de programa pdb  
  
 Este error puede deberse a un error del disco.  
  
 En Visual C\+\+ .NET 2002, deberá establecerse correctamente la configuración regional del usuario cuando el nombre de archivo \(o la ruta de acceso al directorio con el nombre de archivo\) contenga caracteres MBCS.  Establecer la configuración regional del sistema no basta; debe establecerse también la del usuario para procesar caracteres MBCS.  
  
 Para obtener más información, vea [http:\/\/support.microsoft.com\/default.aspx?scid\=kb;en\-us;246007](http://support.microsoft.com/default.aspx?scid=kb;en-us;246007).