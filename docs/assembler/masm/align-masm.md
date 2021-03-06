---
title: ALIGN (MASM)
ms.date: 12/17/2019
f1_keywords:
- align
helpviewer_keywords:
- ALIGN directive
ms.assetid: 1c386b23-439f-4ec3-a6de-74427b25e47f
ms.openlocfilehash: 700721768deaf92e88b32a97e68c6e017219d19d
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75316595"
---
# <a name="align"></a>ALIGN

La directiva **align** alinea el siguiente elemento de datos o instrucción en una dirección que es un múltiplo de su parámetro. El parámetro debe ser una potencia de 2 (por ejemplo, 1, 2, 4, etc.) que sea menor o igual que la alineación del segmento.

## <a name="syntax"></a>Sintaxis

> **Align** ⟦*constantExpression*⟧

## <a name="remarks"></a>Notas

La directiva **align** permite especificar el desplazamiento inicial de un elemento de datos o una instrucción. Los datos alineados pueden mejorar el rendimiento, a costa del espacio desperdiciado entre los elementos de datos. Se pueden observar grandes mejoras de rendimiento cuando los accesos a datos se encuentran en límites que caben dentro de las líneas de caché. Los accesos a los límites naturales para tipos nativos significan menos tiempo invertido en microcódigo de realineación de hardware interno.

La necesidad de instrucciones alineadas es poco frecuente en los procesadores modernos que usan un modelo de direccionamiento plano, pero es posible que sea necesario para saltar destinos en código anterior para otros modelos de direccionamiento.

Cuando se alinean los datos, el espacio omitido se rellena con ceros. Cuando las instrucciones están alineadas, el espacio omitido se rellena con las instrucciones NOP de tamaño adecuado.

## <a name="see-also"></a>Vea también

[Incluso](even.md)\
[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
