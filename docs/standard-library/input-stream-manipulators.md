---
title: Manipuladores de flujos de entrada
ms.date: 11/04/2016
helpviewer_keywords:
- input streams, manipulators
- input stream objects
ms.assetid: 0addcacb-7b7b-4d70-9775-a59abc400fb3
ms.openlocfilehash: d9a6f00f1b5a52d4d388ace376676b45547bdd49
ms.sourcegitcommit: 0dcab746c49f13946b0a7317fc9769130969e76d
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/24/2019
ms.locfileid: "68451027"
---
# <a name="input-stream-manipulators"></a>Manipuladores de flujos de entrada

Muchos manipuladores, como [setprecision](../standard-library/iomanip-functions.md#setprecision), se definen para la clase `ios` y, por tanto, se aplican a los flujos de entrada. Pero unos pocos manipuladores afectan realmente a los objetos de flujo de entrada. Entre aquellos que lo hacen, los más importantes son los manipuladores de base, `dec`, `oct`, y `hex`, que determinan la base de conversión que se usa con números del flujo de entrada.

En la extracción, el manipulador `hex` permite el procesamiento de diversos formatos de entrada. Por ejemplo, c, C, 0xc, 0xC, 0Xc y 0XC se interpretan como el entero decimal 12. Cualquier carácter distinto de 0 a 9, de A a F, de a a f, x y X termina la conversión numérica. Por lo tanto, la secuencia `"124n5"` se convierte en el número 124 con el conjunto de bits [basic_ios::fail](../standard-library/basic-ios-class.md#fail).

## <a name="see-also"></a>Vea también

[Flujos de entrada](../standard-library/input-streams.md)
