---
title: COMM | Documentos de Microsoft
ms.custom: ''
ms.date: 05/22/2018
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
ms.openlocfilehash: 1df6c729ab130a7ff38d7f7cf83224e7425e7dba
ms.sourcegitcommit: da7b7533d1a4dc141cc0f09149e4e4196f2fe329
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/23/2018
---
# <a name="comm"></a>COMM

Crea una variable comunes con los atributos especificados en *definición*.

## <a name="syntax"></a>Sintaxis

> **COMM** *definición* [, *definición*]...

## <a name="remarks"></a>Comentarios

Variables comunes se asignan mediante el enlazador y no se puede inicializar. Esto significa que no puede depender de la ubicación o secuencia de dichas variables.

Cada *definición* tiene la forma siguiente:

[*langtype*] [**NEAR** &#124; **lejano**] _etiqueta_**:**_tipo_[**:**_recuento_]

Opcional *langtype* establece las convenciones de nomenclatura para el nombre que sigue. Invalida cualquier idioma especificado por el **. MODELO** directiva. Opcional **NEAR** o **lejano** reemplazar el modelo de memoria actual. El *etiqueta* es el nombre de la variable. El *tipo* puede ser cualquier especificador de tipo ([bytes](../../assembler/masm/byte-masm.md), [WORD](../../assembler/masm/word.md), y así sucesivamente) o un entero que especifica el número de bytes. Opcional *recuento* especifica el número de elementos en el objeto de datos declarado; el valor predeterminado es uno.

## <a name="example"></a>Ejemplo

Este ejemplo crea una matriz de elementos de 512 bytes:

```masm
COMM FAR ByteArray:BYTE:512
```

## <a name="see-also"></a>Vea también

[Referencia de directivas](../../assembler/masm/directives-reference.md)
