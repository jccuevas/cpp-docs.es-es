---
title: Error del compilador de recursos RW2001 | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- RW2001
dev_langs:
- C++
helpviewer_keywords:
- RW2001
ms.assetid: 963bdc7d-6ebe-4378-8bbc-47dfcf5d330c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 077260b615d0a5adf32278d8857df5b8f74b7e5f
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33321105"
---
# <a name="resource-compiler-error-rw2001"></a>Error del compilador de recursos RW2001
Directiva no válida en el archivo RC preprocesado  
  
 El archivo RC contiene un **#pragma** directiva.  
  
 Use la **#ifndef** directiva de preprocesador con la **RC_INVOKED** constante que define el compilador de recursos cuando se procesa un archivo de inclusión. Lugar la **#pragma** directiva dentro de un bloque de código que no procesan cuando el **RC_INVOKED** se define la constante. Código del bloque se procesa únicamente por el compilador de C o C++ y no por el compilador de recursos. El código de ejemplo siguiente muestra esta técnica:  
  
```  
#ifndef RC_INVOKED  
#pragma pack(2)  // C/C++ only, ignored by Resource Compiler  
#endif  
```  
  
 El **#pragma** directiva de preprocesador no tiene ningún significado una. Archivo RC. El **#include** directiva de preprocesador se usa con frecuencia en una. Archivo RC para incluir un archivo de encabezado (un archivo de encabezado personalizado basado en el proyecto o un archivo de encabezado estándar proporcionado por Microsoft con uno de sus productos). Algunos de estos archivos de inclusión contienen la **#pragma** directiva. Dado que un archivo de encabezado puede incluir uno o varios otros archivos de encabezado, el archivo que contiene el infractora **#pragma** directiva puede no ser tan evidente.  
  
 El **#ifndef RC_INVOKED** técnica puede controlar archivos de encabezado en los archivos de encabezado basados en proyectos de inclusión.