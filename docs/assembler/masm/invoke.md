---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: 7a005e5e70a2696ca89fb0ad1a3ff02aab8ffe5a
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75317193"
---
# <a name="invoke"></a>INVOKE

(solo para MASM de 32 bits). Llama al procedimiento en la dirección proporcionada por la *expresión*, pasando los argumentos en la pila o en registros según las convenciones de llamada estándar del tipo de lenguaje.     

## <a name="syntax"></a>Sintaxis

> **Invocar** *expresión* ⟦ __,__ *argumento* ... ⟧

## <a name="remarks"></a>Notas

Cada argumento que se pasa al procedimiento puede ser una expresión, un par de registros o una expresión de dirección (una expresión precedida por **addr**).

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
