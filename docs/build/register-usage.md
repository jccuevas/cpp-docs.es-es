---
title: Uso de registros | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
ms.assetid: ce58e2cf-afd3-4068-980e-28a209298265
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4c77469a8cef03827101f4bf367c00a3bb440820
ms.sourcegitcommit: 4fc6869067d533b175207befd2dc60346afee285
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225224"
---
# <a name="register-usage"></a>Uso de registros

La arquitectura proporciona para 16 registros de uso generales (en adelante como registros de enteros), así como 16 registros de XMM/YMM de x64 registra disponibles para su uso de punto flotante. Los registros volátiles son registros residuales que el llamador da por hecho que van a destruirse a lo largo de la llamada. En cuanto a los registros no volátiles, es necesarios conservar sus valores a lo largo de la llamada de función, y el destinatario de la llamada debe guardarlos si se usan.

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
|XMM6:XMM15, YMM6:YMM15|No volátil (XMM), volátil (mitad superior de YMM)|Deben conservarse por destinatario. El llamador debe conservar los registros de YMM según sea necesario.|

En la salida de la función y en la entrada de la función a las llamadas de biblioteca en tiempo de ejecución de C y llamadas del sistema de Windows, la marca de dirección de la CPU se espera marcas register se va a borrar.

## <a name="see-also"></a>Vea también

- [Convenciones de software x64](../build/x64-software-conventions.md)
- [__vectorcall](../cpp/vectorcall.md)
- [Marca de dirección](../c-runtime-library/direction-flag.md)
