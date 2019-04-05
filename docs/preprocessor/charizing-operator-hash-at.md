---
title: Operador de conversión a caracteres (#@)
ms.date: 11/04/2016
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: c9acc9b9872e096cd441b950632c341e975fecb8
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59034340"
---
# <a name="charizing-operator-"></a>Operador de conversión a caracteres (#@)
**Específicos de Microsoft**

El operador charizing solo puede utilizarse con argumentos de macros. Si `#@` precede a un parámetro formal en la definición de la macro, el argumento real está entre comillas simples y se tratan como un carácter cuando se expande la macro. Por ejemplo:

```
#define makechar(x)  #@x
```

hace que la instrucción

```
a = makechar(b);
```

se expanda a

```
a = 'b';
```

El carácter de comilla simple no se puede utilizar con el operador charizing.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Operadores de preprocesador](../preprocessor/preprocessor-operators.md)