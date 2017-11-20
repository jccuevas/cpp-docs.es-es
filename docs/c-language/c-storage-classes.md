---
title: Clases de almacenamiento de C | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- static variables, lifetime
- storage classes
- lifetime, variables
- specifiers, storage class
- storage class specifiers, C storage classes
- storage duration
ms.assetid: 893fb929-f7a9-43dc-a0b3-29cb1ef845c1
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: afec3ea0d88ff7ede9c498a270e2806a4ceb79e8
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="c-storage-classes"></a>Clases de almacenamiento de C
La "clase de almacenamiento" de una variable determina si el elemento tiene una duración "global" o "local". C llama a estas dos duraciones "static" y "automatic". Un elemento con una duración global existe y tiene un valor a lo largo de la ejecución del programa. Todas las funciones tienen duraciones globales.  
  
 A las variables automáticas, o a las variables con duraciones locales, se les asigna un nuevo almacenamiento cada vez que el control de ejecución pasa al bloque en que están definidas. Cuando la ejecución realiza una devolución, las variables dejan de tener valores significativos.  
  
 C proporciona los especificadores de clase de almacenamiento siguientes:  
  
## <a name="syntax"></a>Sintaxis  
 *storage-class-specifier*:  
 **auto**  
  
 **register**  
  
 **static**  
  
 **extern**  
  
 **typedef**  
  
 **__declspec** ( *extended-decl-modifier-seq* ) /* Específico de Microsoft \*/  
  
 A excepción de `__declspec`, solo puede utilizar un *storage-class-specifier* en *declaration-specifier* en una declaración. Si no se crea ninguna especificación de clase de almacenamiento, las declaraciones dentro de un bloque crean objetos automáticos.  
  
 Los elementos declarados con el especificador **auto** o **register** tienen duraciones locales. Los elementos declarados con el especificador **static** o `extern` tienen duraciones globales.  
  
 Como `typedef` y `__declspec` son semánticamente diferentes de los otros cuatro elementos terminales *storage-class-specifier*, se tratan por separado. Para obtener información específica sobre `typedef`, vea [Declaraciones typedef](../c-language/typedef-declarations.md). Para obtener información específica sobre `__declspec`, vea [Atributos extendidos de clase de almacenamiento](../c-language/c-extended-storage-class-attributes.md).  
  
 La colocación de declaraciones de variable y de función dentro de los archivos de código fuente también afecta a la visibilidad y la clase de almacenamiento. Las declaraciones que están fuera de todas las definiciones de función se dice que aparecen en el "nivel externo". Las declaraciones que están dentro de las definiciones de función aparecen en el "nivel interno".  
  
 El significado exacto de cada especificador de clase de almacenamiento depende de dos factores:  
  
-   Que la declaración aparezca en el nivel externo o interno  
  
-   Que el elemento que se va a declarar sea una variable o una función  
  
 En [Especificadores de clase de almacenamiento para declaraciones de nivel externo](../c-language/storage-class-specifiers-for-external-level-declarations.md) y [Especificadores de clase de almacenamiento para declaraciones de nivel interno](../c-language/storage-class-specifiers-for-internal-level-declarations.md), se describen los elementos terminales *storage-class-specifier* de cada clase de declaración y se explica el comportamiento predeterminado cuando se omite el elemento *storage-class-specifier* de una variable. En [Especificadores de clase de almacenamiento con declaraciones de función](../c-language/storage-class-specifiers-with-function-declarations.md) se describen los especificadores de clase de almacenamiento utilizados con funciones.  
  
## <a name="see-also"></a>Vea también  
 [Declaraciones y tipos](../c-language/declarations-and-types.md)