---
title: COMM | Microsoft Docs
ms.custom: ''
ms.date: 08/30/2018
ms.technology:
- cpp-masm
ms.topic: reference
f1_keywords:
- COMM
dev_langs:
- C++
helpviewer_keywords:
- COMM directive
ms.assetid: a23548c4-ad04-41fa-91da-945f228de742
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87bf6d91de052d7ecaf637100b455e66819c748b
ms.sourcegitcommit: a7046aac86f1c83faba1088c80698474e25fe7c3
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/04/2018
ms.locfileid: "43690037"
---
# <a name="comm"></a>COMM

Crea una variable comunal con los atributos especificados en *definición*.

## <a name="syntax"></a>Sintaxis

> **COMM** *definición* [, *definición*]...

## <a name="remarks"></a>Comentarios

Variables comunes son asignadas por el vinculador y no se puede inicializar. Esto significa que no puede depender de la ubicación o secuencia de dichas variables.

Cada *definición* tiene el formato siguiente:

[*langtype*] [**NEAR** &#124; **lejano**] _etiqueta_**:**_tipo_[**:**_recuento_]

El elemento opcional *langtype* establece las convenciones de nomenclatura para el nombre que sigue. Invalida cualquier idioma especificado por el **. MODELO** directiva. El elemento opcional **NEAR** o **lejano** reemplazar el modelo de memoria actual. El *etiqueta* es el nombre de la variable. El *tipo* puede ser cualquier especificador de tipo ([bytes](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md), y así sucesivamente) o un entero que especifica el número de bytes. El elemento opcional *recuento* especifica el número de elementos en el objeto de datos declarado; el valor predeterminado es uno.

## <a name="example"></a>Ejemplo

Este ejemplo crea una matriz de elementos de 512 bytes:

```asm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)<br/>
