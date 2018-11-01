---
title: no_namespace
ms.date: 11/04/2016
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: b17bf5fb5f44d5453de29febe001f9e8737102b5
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50540444"
---
# <a name="nonamespace"></a>no_namespace
**Específicos de C++**

Especifica que el compilador no genera el espacio de nombres.

## <a name="syntax"></a>Sintaxis

```
no_namespace
```

## <a name="remarks"></a>Comentarios

El contenido de la biblioteca de tipos en el archivo de encabezado `#import` se define normalmente en un espacio de nombres. El espacio de nombres se especifica en el `library` instrucción del archivo IDL original. Si el **no_namespace** atributo se especifica, el compilador no genera este espacio de nombres.

Si desea usar un nombre de espacio de nombres diferente, a continuación, utilice el [rename_namespace](../preprocessor/rename-namespace.md) atributo en su lugar.

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)