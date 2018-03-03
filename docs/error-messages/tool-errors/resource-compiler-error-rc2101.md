---
title: Error del compilador de recursos RC2101 | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: error-reference
f1_keywords:
- RC2101
dev_langs:
- C++
helpviewer_keywords:
- RC2101
ms.assetid: 580f9d74-162f-41e9-9438-ddbe3457c359
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: d08e9ddb7b8cda127b1d05bfef52b52833534cb2
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="resource-compiler-error-rc2101"></a>Error del compilador de recursos RC2101
Directiva no válida en el archivo RC preprocesado  
  
 El archivo del compilador de recursos contiene una **#pragma** directiva.  
  
 Use la **#ifndef** directiva de preprocesador con la constante RC_INVOKED que define el compilador de recursos cuando se procesa un archivo de inclusión. Lugar la **#pragma** directiva dentro de un bloque de código que no se procesa cuando se define la constante RC_INVOKED. Código del bloque se procesa únicamente por el compilador de C o C++ y no por el compilador de recursos. El código de ejemplo siguiente muestra esta técnica:  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 El **#pragma** directiva de preprocesador no tiene ningún significado una. Archivo RC. El **#include** directiva de preprocesador se usa con frecuencia en una. Archivo RC para incluir un archivo de encabezado (un archivo de encabezado personalizado basado en el proyecto o un archivo de encabezado estándar proporcionado por Microsoft con uno de sus productos). Algunos de estos archivos de inclusión contienen la **#pragma** directiva. Dado que un archivo de encabezado puede incluir uno o varios otros archivos de encabezado, el archivo que contiene el infractora **#pragma** directiva puede no ser tan evidente.  
  
 El **#ifndef** RC_INVOKED puede controlar archivos de encabezado en los archivos de encabezado basados en proyectos de inclusión.