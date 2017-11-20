---
title: Tipo char | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- type char
- unsigned char keyword [C]
- char keyword [C]
ms.assetid: a5da0866-e780-4793-be87-15a8426e7ea0
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.openlocfilehash: c1046de3ca21cecf99c070a24a041e5c627d2961
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2017
---
# <a name="type-char"></a>Tipo char
El tipo `char` se usa para almacenar el valor entero de un miembro del juego de caracteres que se puede representar. Ese valor entero es el código ASCII correspondiente al carácter especificado.  
  
 **Específicos de Microsoft**  
  
 Los valores de carácter de tipo `unsigned char` tienen un intervalo de 0 a 0xFF hexadecimal. **signed char** tiene un intervalo de 0x80 a 0x7F. Estos intervalos se traducen a 0 a 255 decimal y -128 a +127 decimal, respectivamente. La opción del compilador /J cambia el valor predeterminado de **signed** a `unsigned`.  
  
 **FIN de Específicos de Microsoft**  
  
## <a name="see-also"></a>Vea también  
 [Almacenamiento de tipos básicos](../c-language/storage-of-basic-types.md)