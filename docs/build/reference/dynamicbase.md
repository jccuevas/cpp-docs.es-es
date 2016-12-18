---
title: "/DYNAMICBASE | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "/dynamicbase"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/DYNAMICBASE (opción de editbin)"
  - "DYNAMICBASE (opción de editbin)"
  - "-DYNAMICBASE (opción de editbin)"
ms.assetid: edb3df90-7b07-42fb-a94a-f5a4c1d325d6
caps.latest.revision: 6
caps.handback.revision: 6
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /DYNAMICBASE
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica si una imagen ejecutable se puede reorganizar aleatoriamente en el momento de la carga con la selección aleatoria del diseño del espacio de direcciones \(ASLR\).  
  
## Sintaxis  
  
```  
  
/DYNAMICBASE[:NO]  
```  
  
## Comentarios  
 De forma predeterminada, el enlazador establece la opción **\/DYNAMICBASE**.  
  
 Esta opción modifica el encabezado de una imagen ejecutable para indicar si el cargador puede reorganizar aleatoriamente la imagen en el momento de la carga.  
  
 ASLR se admite en Windows Vista, Windows Server 2008, Windows 7, Windows 8 y Windows Server 2012.  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)   
 [Defensas de seguridad de software de ISV de Windows](http://msdn.microsoft.com/library/bb430720.aspx)