---
title: Manipuladores de flujos de entrada | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: "8"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 17242528dd2be4a72a763f34ee651fc170fea58c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="input-stream-manipulators"></a>Manipuladores de flujos de entrada
Muchos manipuladores, como [setprecision]--brokenlink--(../Topic/not%20found:3ddde610-70cc-4cfa-8a89-3e83d1d356a8.md#setprecision), están definidos para la clase `ios` y, por tanto, se aplican a flujos de entrada. Pero unos pocos manipuladores afectan realmente a los objetos de flujo de entrada. Entre aquellos que lo hacen, los más importantes son los manipuladores de base, `dec`, `oct`, y `hex`, que determinan la base de conversión que se usa con números del flujo de entrada.  
  
 En la extracción, el manipulador `hex` permite el procesamiento de diversos formatos de entrada. Por ejemplo, c, C, 0xc, 0xC, 0Xc y 0XC se interpretan como el entero decimal 12. Cualquier carácter distinto de 0 a 9, de A a F, de a a f, x y X termina la conversión numérica. Por lo tanto, la secuencia `"124n5"` se convierte en el número 124 con el conjunto de bits [basic_ios::fail](../standard-library/basic-ios-class.md#fail).  
  
## <a name="see-also"></a>Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)

