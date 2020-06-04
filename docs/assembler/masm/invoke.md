---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: ba1377359ba9bc960e5d7d2a55df15adfe0d5d33
ms.sourcegitcommit: 8e285a766523e653aeeb34d412dc6f615ef7b17b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/21/2020
ms.locfileid: "80076224"
---
# <a name="invoke"></a>INVOKE

(solo para MASM de 32 bits). Llama al procedimiento en la dirección proporcionada por la *expresión*, pasando los argumentos en la pila o en registros según las convenciones de llamada estándar del tipo de lenguaje.

## <a name="syntax"></a>Sintaxis

> **Invocar** *expresión* ⟦ __,__ *argumento* ... ⟧

## <a name="remarks"></a>Observaciones

Cada argumento que se pasa al procedimiento puede ser una expresión, un par de registros o una expresión de dirección (una expresión precedida por **addr**).

## <a name="see-also"></a>Consulte también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
