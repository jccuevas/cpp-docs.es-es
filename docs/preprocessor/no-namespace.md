---
title: no_namespace
ms.date: 11/04/2016
f1_keywords:
- no_namespace
helpviewer_keywords:
- no_namespace attribute
ms.assetid: 5d81b741-a558-451b-b493-1f3b18967337
ms.openlocfilehash: f6bd60de02bf0166d5cf0b0cd1bc1de56ceda5bf
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59028722"
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

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)