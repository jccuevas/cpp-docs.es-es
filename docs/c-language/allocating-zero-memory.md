---
title: "Asignación de memoria cero | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- memory allocation, zero memory
- zero memory
ms.assetid: 768f2ab9-83a1-4887-8eb5-c094c18489a8
caps.latest.revision: "6"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: 9708f8939ff32f9320e7c8e803753e801ce9448f
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="allocating-zero-memory"></a>Asignación de memoria cero
**ANSI 4.10.3** El comportamiento de la función `calloc`, `malloc` o `realloc` si el tamaño solicitado es cero  
  
 Las funciones `calloc`, `malloc` y `realloc` aceptan cero como argumento. No se asigna ninguna memoria real, pero se devuelve un puntero válido y el bloque de memoria se puede modificar después mediante realloc.  
  
## <a name="see-also"></a>Vea también  
 [Funciones de la biblioteca](../c-language/library-functions.md)