---
title: "/ALLOWISOLATION | Microsoft Docs"
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
  - "/ALLOWISOLATION"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "/ALLOWISOLATION (opción de editbin)"
  - "ALLOWISOLATION (opción de editbin)"
  - "-ALLOWISOLATION (opción de editbin)"
ms.assetid: 91430344-f64f-491a-a5a5-7ea3b21cbe68
caps.latest.revision: 11
caps.handback.revision: 11
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
---
# /ALLOWISOLATION
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Especifica el comportamiento de la búsqueda de manifiesto.  
  
## Sintaxis  
  
```  
  
/ALLOWISOLATION[:NO]  
```  
  
## Comentarios  
 **\/ALLOWISOLATION** hace que el sistema operativo realice cargas y búsquedas de manifiestos.  
  
 **\/ALLOWISOLATION** es el valor predeterminado.  
  
 **\/ALLOWISOLATION:NO** indica que los archivos ejecutables deben cargarse como si no existiera ningún manifiesto y hace que [Referencia de EDITBIN](../../build/reference/editbin-reference.md) establezca el bit de `IMAGE_DLLCHARACTERISTICS_NO_ISOLATION` en el campo `DllCharacteristics` del encabezado opcional.  
  
 Cuando se deshabilita el aislamiento para un ejecutable, el cargador de Windows no busca ningún manifiesto de aplicación para el proceso recién creado.  El nuevo proceso no tiene un contexto de activación predeterminado, ni siquiera si existe un manifiesto en el propio ejecutable, o existe un manifiesto con el nombre *nombre\-ejecutable*.exe.manifest.  
  
## Vea también  
 [Opciones de EDITBIN](../../build/reference/editbin-options.md)   
 [\/ALLOWISOLATION \(Manifestar bucle\)](../../build/reference/allowisolation-manifest-lookup.md)   
 [Referencia de archivos de manifiesto](http://msdn.microsoft.com/library/aa375632.aspx)