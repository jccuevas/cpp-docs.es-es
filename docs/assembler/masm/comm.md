---
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 0ea02806cae3295af0846baa6c4e9049d54c271b
ms.sourcegitcommit: 0781c69b22797c41630601a176b9ea541be4f2a3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/20/2019
ms.locfileid: "75315178"
---
# <a name="comm"></a>COMM

Crea una variable Communal con los atributos especificados en la *definición*.

## <a name="syntax"></a>Sintaxis

> *Definición* de COMM ⟦ __,__ *definición* ... ⟧

## <a name="remarks"></a>Notas

El enlazador asigna las variables Communal y no se puede inicializar. Esto significa que no puede depender de la ubicación o secuencia de dichas variables.

Cada *definición* tiene el formato siguiente:

⟦*Language-Type*⟧ ⟦**Near** | **Far**⟧ _Label_ **:** _Type_⟦ **:** _Count_⟧

Los argumentos de *tipo de idioma*, **Near**y **Far** solo son válidos en MASM de 32 bits.

El *tipo de lenguaje* opcional establece las convenciones de nomenclatura para el nombre que sigue. Invalida cualquier lenguaje especificado por **.** Directiva de modelo. La opción opcional **Near** o **Far** invalida el modelo de memoria actual. La *etiqueta* es el nombre de la variable. El *tipo* puede ser cualquier especificador de tipo ([byte](byte-masm.md), [Word](word.md), etc.) o un entero que especifique el número de bytes. El *recuento* opcional especifica el número de elementos del objeto de datos declarado. El *recuento* predeterminado es uno.

## <a name="example"></a>Ejemplo

En este ejemplo se crea una matriz de elementos de 512 BYTEs:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)\
[Gramática BNF de MASM](masm-bnf-grammar.md)
