---
title: Manipuladores de flujos de entrada | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 30f642dc4942491bd73265e3d647d3281f97c1e7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33842210"
---
# <a name="input-stream-manipulators"></a>Manipuladores de flujos de entrada

Muchos de los manipuladores, como [setprecision](../standard-library/iomanip-functions.md#setprecision), se definen para el `ios` clase y, por tanto, se aplican a flujos de entrada. Pero unos pocos manipuladores afectan realmente a los objetos de flujo de entrada. Entre aquellos que lo hacen, los más importantes son los manipuladores de base, `dec`, `oct`, y `hex`, que determinan la base de conversión que se usa con números del flujo de entrada.

En la extracción, el manipulador `hex` permite el procesamiento de diversos formatos de entrada. Por ejemplo, c, C, 0xc, 0xC, 0Xc y 0XC se interpretan como el entero decimal 12. Cualquier carácter distinto de 0 a 9, de A a F, de a a f, x y X termina la conversión numérica. Por lo tanto, la secuencia `"124n5"` se convierte en el número 124 con el conjunto de bits [basic_ios::fail](../standard-library/basic-ios-class.md#fail).

## <a name="see-also"></a>Vea también

[Flujos de entrada](../standard-library/input-streams.md)<br/>
