---
title: INVOKE
ms.date: 08/30/2018
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: efa8f710701e15845c3a6a22ba024c9cf1882457
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50579028"
---
# <a name="invoke"></a>INVOKE

Llama al procedimiento en la dirección proporcionada por *expresión*, pasando los argumentos en la pila o en los registros según las convenciones de llamada estándares del tipo de lenguaje.

## <a name="syntax"></a>Sintaxis

> INVOKE *expresión* [[, *argumentos*]]

## <a name="remarks"></a>Comentarios

Cada argumento pasado al procedimiento puede ser una expresión, un par de registro o una expresión de dirección (precedido de una expresión `ADDR`).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>