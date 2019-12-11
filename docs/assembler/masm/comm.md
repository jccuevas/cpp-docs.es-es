---
title: COMM
ms.date: 12/06/2019
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: 93e7c891b1c964eca5b3ff7fd15956ef25ea05e6
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/10/2019
ms.locfileid: "74987945"
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

El *tipo de lenguaje* opcional establece las convenciones de nomenclatura para el nombre que sigue. Invalida cualquier lenguaje especificado por **.** Directiva de modelo. La opción opcional **Near** o **Far** invalida el modelo de memoria actual. La *etiqueta* es el nombre de la variable. El *tipo* puede ser cualquier especificador de tipo ([byte](../../assembler/masm/byte-masm.md), [Word](../../assembler/masm/word.md), etc.) o un entero que especifique el número de bytes. El *recuento* opcional especifica el número de elementos del objeto de datos declarado. El *recuento* predeterminado es uno.

## <a name="example"></a>Ejemplo

En este ejemplo se crea una matriz de elementos de 512 BYTEs:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
