---
title: Manipuladores de flujos de entrada | Microsoft Docs
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-standard-libraries
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: ce3f1b99fe44d07a8793501c800f32077509ec0d
ms.sourcegitcommit: 185e11ab93af56ffc650fe42fb5ccdf1683e3847
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 01/29/2018
---
# <a name="input-stream-manipulators"></a>Manipuladores de flujos de entrada
Muchos de los manipuladores, como [setprecision](../standard-library/iomanip-functions.md#setprecision), se definen para el `ios` clase y, por tanto, se aplican a flujos de entrada. Pero unos pocos manipuladores afectan realmente a los objetos de flujo de entrada. Entre aquellos que lo hacen, los más importantes son los manipuladores de base, `dec`, `oct`, y `hex`, que determinan la base de conversión que se usa con números del flujo de entrada.  
  
 En la extracción, el manipulador `hex` permite el procesamiento de diversos formatos de entrada. Por ejemplo, c, C, 0xc, 0xC, 0Xc y 0XC se interpretan como el entero decimal 12. Cualquier carácter distinto de 0 a 9, de A a F, de a a f, x y X termina la conversión numérica. Por lo tanto, la secuencia `"124n5"` se convierte en el número 124 con el conjunto de bits [basic_ios::fail](../standard-library/basic-ios-class.md#fail).  
  
## <a name="see-also"></a>Vea también  
 [Flujos de entrada](../standard-library/input-streams.md)

