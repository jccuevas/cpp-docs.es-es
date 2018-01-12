---
title: Error irrecuperable del compilador de recursos RC1052 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords: RC1052
dev_langs: C++
helpviewer_keywords: RC1052
ms.assetid: 59803673-492b-44fa-80fa-df93b8aaf9fb
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 0546441022d8e2b487d83e291574020665cdaf4c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-fatal-error-rc1052"></a>Error irrecuperable del compilador de recursos RC1052
límite del compilador: los bloques #if o #ifdef están demasiado anidados  
  
 El programa superó el máximo permitido de niveles de anidamiento para las directivas `#if` y `#ifdef`.  
  
 Este error puede deberse a los archivos de inclusión que utilizan estas directivas de preprocesador.  
  
 Para solucionar este problema, reduzca el número de directivas `#if` y `#ifdef` anidadas en el archivo de recursos. Si el problema está causado por archivos de encabezado incluidos en el archivo de recursos, reduzca el número de directivas `#if` y `#ifdef` anidadas en los archivos de encabezado. Si no es posible, considere la posibilidad de crear e incluir un nuevo archivo de encabezado en el archivo de recursos, ejecutando el preprocesador en los archivos de encabezado incluidos. Para obtener más información, consulte el [/P (Preprocesar para un archivo)](../../build/reference/p-preprocess-to-a-file.md) opción del compilador.