---
title: atributo de importación no_namespace
ms.date: 08/29/2019
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: ba52aed69cdbb46c135e6de5078d718e93f99c87
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70220732"
---
# <a name="no_namespace-import-attribute"></a>atributo de importación no_namespace

**C++Cuestión**

Especifica que el compilador no genera un nombre de espacio de nombres.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos* **no_namespace**

## <a name="remarks"></a>Comentarios

El contenido de la biblioteca de tipos en el archivo de encabezado `#import` se define normalmente en un espacio de nombres. El nombre del espacio de nombres se `library` especifica en la instrucción del archivo IDL original. Si se especifica el atributo **no_namespace** , el compilador no genera este espacio de nombres.

Si desea utilizar un nombre de espacio de nombres diferente, utilice en su lugar el atributo [rename_namespace](../preprocessor/rename-namespace.md) .

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
