---
title: "Error de las herramientas del vinculador LNK1309 | Microsoft Docs"
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
  - "LNK1309"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "LNK1309"
ms.assetid: 10146071-883f-4849-97d1-c7468f90efbb
caps.latest.revision: 7
caps.handback.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# Error de las herramientas del vinculador LNK1309
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

módulo tipo1 detectado; no válido con el modificador \/CLRIMAGETYPE:tipo2  
  
 Se ha solicitado un tipo de imagen CLR con **\/CLRIMAGETYPE** pero el vinculador no ha podido generar ninguna imagen de ese tipo porque uno o varios módulos no eran compatibles con ese tipo.  
  
 Por ejemplo, se producirá el error LNK1309 si se especifica **\/CLRIMAGETYPE:safe** y se pasa un módulo creado con **\/clr:pure**.  
  
 También se producirá el error LNK1309 si se intenta compilar una aplicación pura CLR que no sea de plena confianza utilizando ptrustu \[d\] .lib.  Para obtener información sobre cómo se crea una aplicación que no sea de plena confianza, vea [Cómo: Crear una aplicación de confianza parcial quitando la dependencia de la DLL de la biblioteca CRT](../../dotnet/create-a-partially-trusted-application.md).  
  
 Para obtener más información, vea [\/clr \(Compilación de Common Language Runtime\)](../../build/reference/clr-common-language-runtime-compilation.md) y [\/CLRIMAGETYPE \(Especificar tipo de imagen CLR\)](../../build/reference/clrimagetype-specify-type-of-clr-image.md).