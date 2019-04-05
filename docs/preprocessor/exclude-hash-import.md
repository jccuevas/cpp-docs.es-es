---
title: exclude (#import)
ms.date: 10/18/2018
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: d6a320089d5954b2cf1d0d96ae1f37656f2ddd58
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59032393"
---
# <a name="exclude-import"></a>excluir (\#importar)

**Específicos de C++**

Excluye elementos de los archivos de encabezado de la biblioteca de tipos que se generan.

## <a name="syntax"></a>Sintaxis

```
exclude("Name1"[, "Name2",...])
```

### <a name="parameters"></a>Parámetros

*Nombre1*<br/>
Primer elemento que se excluirá.

*Nombre2*<br/>
Segundo elemento que se excluirá (si es necesario).

## <a name="remarks"></a>Comentarios

Las bibliotecas de tipos pueden incluir definiciones de elementos definidos en encabezados de sistema u otras bibliotecas de tipos. Este atributo puede tomar cualquier número de argumentos, cada uno de los cuales es un elemento de nivel superior de la biblioteca de tipos que se va a excluir.

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)