---
title: Desplazamientos a la derecha | Microsoft Docs
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
ms.assetid: c878e97d-ea3c-4c6b-90a8-b1b24b2d5b19
caps.latest.revision: 7
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 16d1bf59dfd4b3ef5f037aed9c0f6febfdf1a2e8
ms.openlocfilehash: cee551dfd0dbac11110a945edee21af6636138bc
ms.contentlocale: es-es
ms.lasthandoff: 10/09/2017

---
# <a name="right-shifts"></a>Desplazamientos a la derecha
El resultado de un desplazamiento a la derecha de un tipo entero con signo de valor negativo  
  
 Cuando se desplaza a la derecha un valor negativo se produce la mitad del valor absoluto, redondeado a la baja. Por ejemplo, un valor `short` con signo de -253 (hexadecimal 0xFF03, binario 11111111 00000011) desplazado a la derecha un bit produce -127 (hexadecimal 0xFF81, binario 11111111 10000001). Un 253 positivo desplazado a la derecha produce + 126.  
  
 Los desplazamientos a la derecha preservan el bit de signo de los tipos enteros con signo. Cuando un entero con signo se desplaza a la derecha, el bit más significativo permanece establecido. Por ejemplo, si 0xF0000000 es un `int` con signo, un desplazamiento a la derecha produce 0xF8000000. Desplazar un `int` negativo a la derecha 32 veces produce 0xFFFFFFFF.  
  
 Cuando un entero sin signo se desplaza a la derecha, el bit más significativo se borra. Por ejemplo, si 0xF000 es sin signo, el resultado es 0x7800. Desplazar un `unsigned` o `int` positivo a la derecha 32 veces produce 0 x 00000000.  
  
## <a name="see-also"></a>Vea también  
 [Enteros](../c-language/integers.md)
