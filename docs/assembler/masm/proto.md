---
title: PROTO
ms.date: 12/06/2019
f1_keywords:
- PROTO
helpviewer_keywords:
- PROTO directive
ms.assetid: 0487ee16-9dc7-43d1-9445-cd1601f5a080
ms.openlocfilehash: 3963fa29050653d1706222d33734c4b5f2a17919
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75318649"
---
# <a name="proto"></a>PROTO

Prototipos de una función o un procedimiento. Puede llamar a la función prototipo de la Directiva PROTO mediante la directiva [INVOKE](invoke.md) .

## <a name="syntax"></a>Sintaxis

> *etiqueta* **proto** ⟦*Distance*⟧ ⟦*Language-Type*⟧ ⟦ __,__ ⟦*parámetro*⟧ __:__ *Tag* ... ⟧

### <a name="parameters"></a>Parameters

\ de *etiqueta*
Nombre de la función prototipo.

*distancia* (solo para MASM de 32 bits). \
Opta Se usa en los modelos de memoria de 16 bits para reemplazar el valor predeterminado e indicar llamadas **cercanas** o **lejanas** .

*tipo de idioma* (solo MASM de 32 bits). \
Opta Establece la llamada y la Convención de nomenclatura para los procedimientos y símbolos públicos. Las convenciones admitidas son:

- modelo **plano** de 32 bits: **C**, **Stdcall**

- modelos de 16 bits: **C**, **Basic**, **Fortran**, **Pascal**, **syscall**, **Stdcall**

\ de *parámetros*
Nombre opcional de un parámetro de función.

\ de *etiquetas*
El tipo de un parámetro de función.

Los parámetros de *parámetro* y *etiqueta* pueden aparecer varias veces, una vez para cada argumento pasado.

## <a name="example"></a>Ejemplo

En este ejemplo se muestra una declaración de **proto** para una función denominada `addup3` que usa una llamada **Near** para reemplazar el valor predeterminado del modelo de 16 bits para las llamadas a procedimientos y usa la Convención de llamada de **C** para los parámetros de pila y los valores devueltos. Toma dos argumentos, una **palabra** y un **vararg**.

```MASM
addup3 PROTO NEAR C, argcount:WORD, arg1:VARARG
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[. ](dot-model.md)\ de referencia de modelo
[Gramática BNF de MASM](masm-bnf-grammar.md)
