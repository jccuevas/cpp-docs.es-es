---
title: exclude (#import)
ms.date: 10/18/2018
f1_keywords:
- exclude
helpviewer_keywords:
- exclude attribute
ms.assetid: 0883248a-d4bf-420e-9848-807b28fa976e
ms.openlocfilehash: 1de1376fbe80147bc9fe01ea83bad81912431310
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50498259"
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

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)