---
title: "Error irrecuperable del compilador de recursos RC1052 | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "error-reference"
f1_keywords: 
  - "RC1052"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "RC1052"
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
caps.latest.revision: 7
author: "corob-msft"
ms.author: "corob"
manager: "ghogen"
caps.handback.revision: 7
---
# Error irrecuperable del compilador de recursos RC1052
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

límite del compilador: los bloques \#if o \#ifdef están demasiado anidados  
  
 El programa superó el máximo permitido de niveles de anidamiento para las directivas `#if` y `#ifdef`.  
  
 Este error puede deberse a los archivos de inclusión que utilizan estas directivas de preprocesador.  
  
 Para solucionar este problema, reduzca el número de directivas `#if` y `#ifdef` anidadas en el archivo de recursos.  Si el problema está causado por archivos de encabezado incluidos en el archivo de recursos, reduzca el número de directivas `#if` y `#ifdef` anidadas en los archivos de encabezado.  Si no es posible, considere la posibilidad de crear e incluir un nuevo archivo de encabezado en el archivo de recursos, ejecutando el preprocesador en los archivos de encabezado incluidos.  Para obtener más información, consulte la opción del compilador [\/P \(Preprocesar y escribir en un archivo\)](../../build/reference/p-preprocess-to-a-file.md).