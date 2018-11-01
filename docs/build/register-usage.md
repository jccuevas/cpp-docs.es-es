---
title: Uso de registros
ms.date: 11/04/2016
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
ms.openlocfilehash: fa04318ad4af298f300fbbbad8c01d0df9500ec7
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50629988"
---
# <a name="register-usage"></a>Uso de registros

La arquitectura proporciona para 16 registros de uso general (en adelante como registros de enteros), así como 16 registros de XMM/YMM de x64 registra disponibles para su uso de punto flotante. Los registros volátiles son registros residuales que el llamador da por hecho que van a destruirse a lo largo de la llamada. En cuanto a los registros no volátiles, es necesarios conservar sus valores a lo largo de la llamada de función, y el destinatario de la llamada debe guardarlos si se usan.

## <a name="register-volatility-and-preservation"></a>Registrar la volatilidad y conservación

En la siguiente tabla se explica el uso de cada registro en las llamadas de función:

||||
|-|-|-|
|Registro|Estado|Uso|
|RAX|Volátil|Registro de valor devuelto|
|RCX|Volátil|Primer argumento de entero|
|RDX|Volátil|Segundo argumento de entero|
|R8|Volátil|Tercer argumento de entero|
|R9|Volátil|Cuarto argumento de entero|
|R10:R11|Volátil|El llamador debe conservarlo según sea necesario; utilizado en instrucciones syscall/sysret|
|R12:R15|No volátil|El destinatario de la llamada debe conservarlo|
|RDI|No volátil|El destinatario de la llamada debe conservarlo|
|RSI|No volátil|El destinatario de la llamada debe conservarlo|
|RBX|No volátil|El destinatario de la llamada debe conservarlo|
|RBP|No volátil|Se puede usar como un puntero de marco; el destinatario de la llamada debe conservarlo según sea necesario|
|RSP|No volátil|Puntero de pila|
|XMM0, YMM0|Volátil|Primer argumento de FP; primer argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM1, YMM1|Volátil|Segundo argumento de FP; segundo argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM2, YMM2|Volátil|Tercer argumento de FP; tercer argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM3, YMM3|Volátil|Cuarto argumento de FP; cuarto argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM4, YMM4|Volátil|El llamador debe conservarlo según sea necesario; quinto argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM5, YMM5|Volátil|El llamador debe conservarlo según sea necesario; sexto argumento de tipo vectorial cuando se usa `__vectorcall`|
|XMM6:XMM15, YMM6:YMM15|No volátil (XMM), volátil (mitad superior de YMM)|Deben conservarse por el destinatario. El llamador debe conservar los registros de YMM según sea necesario.|

En la salida de la función y en la entrada de la función a las llamadas de biblioteca en tiempo de ejecución de C y las llamadas del sistema de Windows, la marca de dirección en la CPU register marcas se espera que se puede borrar.

## <a name="see-also"></a>Vea también

- [Convenciones de software x64](../build/x64-software-conventions.md)
- [__vectorcall](../cpp/vectorcall.md)
- [Marca de dirección](../c-runtime-library/direction-flag.md)
