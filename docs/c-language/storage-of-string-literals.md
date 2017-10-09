---
title: Almacenamiento de literales de cadena | Microsoft Docs
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
- string literals, storage
ms.assetid: ba5e4d2c-d456-44b3-a8ca-354af547ac50
caps.latest.revision: 9
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: 2a1a001899e46fbd8894b72f2c8cd806f1834b7e
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="storage-of-string-literals"></a>Almacenamiento de literales de cadena
Los caracteres de una cadena literal se almacenan en orden en ubicaciones de memoria contiguas. Una secuencia de escape (tal como **\\\\** o **\\"**) dentro de un literal de cadena cuenta como un carácter individual. Un carácter null (representado por la secuencia de escape **\0**) se anexa automáticamente y marca el final de cada literal de cadena. (Esto ocurre durante la [fase de conversión](../preprocessor/phases-of-translation.md) 7). Tenga en cuenta que el compilador no puede almacenar dos cadenas idénticas en dos direcciones distintas. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) fuerza al compilador a colocar una única copia de cadenas idénticas en el archivo ejecutable.  
  
## <a name="remarks"></a>Comentarios  
 **Específicos de Microsoft**  
  
 Las cadenas tienen duración de almacenamiento estático. Vea [Clases de almacenamiento](../c-language/c-storage-classes.md) para obtener información sobre la duración del almacenamiento.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Literales de cadena de C](../c-language/c-string-literals.md)
