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
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
ms.translationtype: Human Translation
ms.sourcegitcommit: d6eb43b2e77b11f4c85f6cf7e563fe743d2a7093
ms.openlocfilehash: 8ee698c1db706c45b1b283a33ec95c135907e031
ms.contentlocale: es-es
ms.lasthandoff: 05/18/2017

---
# <a name="storage-of-string-literals"></a>Almacenamiento de literales de cadena
Los caracteres de una cadena literal se almacenan en orden en ubicaciones de memoria contiguas. Una secuencia de escape (tal como **\\\\** o **\\"**) dentro de un literal de cadena cuenta como un carácter individual. Un carácter null (representado por la secuencia de escape **\0**) se anexa automáticamente y marca el final de cada literal de cadena. (Esto ocurre durante la [fase de conversión](../preprocessor/phases-of-translation.md) 7). Tenga en cuenta que el compilador no puede almacenar dos cadenas idénticas en dos direcciones distintas. [/GF](../build/reference/gf-eliminate-duplicate-strings.md) fuerza al compilador a colocar una única copia de cadenas idénticas en el archivo ejecutable.  
  
## <a name="remarks"></a>Comentarios  
 **Específicos de Microsoft**  
  
 Las cadenas tienen duración de almacenamiento estático. Vea [Clases de almacenamiento](../c-language/c-storage-classes.md) para obtener información sobre la duración del almacenamiento.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Literales de cadena de C](../c-language/c-string-literals.md)
