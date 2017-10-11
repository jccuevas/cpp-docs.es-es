---
title: "Especificadores de clase de almacenamiento con declaraciones de función | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- function specifiers, storage class
- declaring functions, specifiers
- external declarations
- specifiers, function
- external linkage, function declarations
- external linkage, storage-class specifiers
ms.assetid: 801d7df2-efa9-4924-a725-274a5654cfd4
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 1073f0eef2a976866f0bacd0cfbe1f7e6f022334
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="storage-class-specifiers-with-function-declarations"></a>Especificadores de clase de almacenamiento con declaraciones de función
Puede utilizar el especificador de clase de almacenamiento **static** o `extern` en declaraciones de función. Las funciones siempre tienen duraciones globales.  
  
 **Específicos de Microsoft**  
  
 Las declaraciones de función en el nivel interno tienen el mismo significado que las declaraciones de función en el nivel externo. Esto significa que una función estará visible desde su punto de declaración en el resto de la unidad de traducción aunque se declare en ámbito local.  
  
 **FIN de Específicos de Microsoft**  
  
 Las reglas de visibilidad para funciones difieren ligeramente de las reglas para variables, del modo siguiente:  
  
-   Una función declarada como **static** solo es visible en el archivo de código fuente en el que está definida. Las funciones del mismo archivo de código fuente pueden llamar a la función **static**, pero las funciones de otros archivos de código fuente no pueden acceder directamente por el nombre. Puede declarar otra función **static** con el mismo nombre en un archivo de código fuente diferente sin conflicto.  
  
-   Las funciones declaradas como `extern` están visibles en todos los archivos de código fuente del programa (a menos que vuelva a declarar la función en cuestión posteriormente como **static**). Cualquier función puede llamar a una función `extern`.  
  
-   Las declaraciones de función que omiten el especificador de clase de almacenamiento son `extern` de forma predeterminada.  
  
 **Específicos de Microsoft**  
  
 Microsoft permite la redefinición de un identificador `extern` como **static**.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Clases de almacenamiento de C](../c-language/c-storage-classes.md)
