---
title: INVOKE
ms.date: 11/05/2019
f1_keywords:
- Invoke
helpviewer_keywords:
- INVOKE directive
ms.assetid: 12d9bb40-33b9-411e-b801-45a1d675967e
ms.openlocfilehash: a5175252364918ca218e81536b29f084f7fd19cc
ms.sourcegitcommit: 9ee5df398bfd30a42739632de3e165874cb675c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/22/2019
ms.locfileid: "74397306"
---
# <a name="invoke-32-bit-masm"></a>INVOKE (MASM de 32 bits)

Llama al procedimiento en la dirección proporcionada por la *expresión*, pasando los argumentos en la pila o en registros según las convenciones de llamada estándar del tipo de lenguaje. (solo para MASM de 32 bits).

## <a name="syntax"></a>Sintaxis

> **Invocar** *expresión* ⟦ __,__ *argumento* ... ⟧

## <a name="remarks"></a>Comentarios

Cada argumento que se pasa al procedimiento puede ser una expresión, un par de registros o una expresión de dirección (una expresión precedida por **addr**).

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)
