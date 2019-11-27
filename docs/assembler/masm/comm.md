---
title: COMM
ms.date: 08/30/2018
f1_keywords:
- COMM
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
ms.openlocfilehash: d36161ba54ca80fc0f576c6f0a7c2a9410bf8075
ms.sourcegitcommit: 3ee06ec53153cf21910fc8cfef78a4f25f9633f3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/26/2019
ms.locfileid: "74541032"
---
# <a name="comm"></a>COMM

Crea una variable Communal con los atributos especificados en la *definición*.

## <a name="syntax"></a>Sintaxis

> *Definición* de COMM ⟦ __,__ *definición* ... ⟧

## <a name="remarks"></a>Notas

El enlazador asigna las variables Communal y no se puede inicializar. Esto significa que no puede depender de la ubicación o secuencia de dichas variables.

Cada *definición* tiene el formato siguiente:

⟦*Language-Type*⟧ ⟦**Near** | **Far**⟧ _Label_ **:** _Type_⟦ **:** _Count_⟧

El *tipo de lenguaje* opcional establece las convenciones de nomenclatura para el nombre que sigue. Invalida cualquier lenguaje especificado por **.** Directiva de modelo. La opción opcional **Near** o **Far** invalida el modelo de memoria actual. La *etiqueta* es el nombre de la variable. El *tipo* puede ser cualquier especificador de tipo ([byte](../../assembler/masm/byte-masm.md), [Word](../../assembler/masm/word.md), etc.) o un entero que especifique el número de bytes. El *recuento* opcional especifica el número de elementos del objeto de datos declarado. El *recuento* predeterminado es uno.

## <a name="example"></a>Ejemplo

En este ejemplo se crea una matriz de elementos de 512 BYTEs:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](directives-reference.md)
