---
title: Operador de conversión a caracteres (#@)
ms.date: 08/29/2019
f1_keywords:
- '#@'
helpviewer_keywords:
- preprocessor, operators
- charizing operator
- '#@ preprocessor operator'
ms.assetid: dee03314-d27c-4063-965c-64756efbef22
ms.openlocfilehash: cb2a4e07287edf5ed2d0850ec7d870c8ef307879
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218532"
---
# <a name="charizing-operator-"></a>Operador de conversión a caracteres (#@)

**Específicos de Microsoft**

El operador charizing solo puede utilizarse con argumentos de macros. Si `#@` precede a un parámetro formal en la definición de la macro, el argumento real se incluye entre comillas simples y se trata como un carácter cuando se expande la macro. Por ejemplo:

```cpp
#define makechar(x)  #@x
```

hace que la instrucción

```cpp
a = makechar(b);
```

se expanda a

```cpp
a = 'b';
```

El carácter de comilla simple`'`() no se puede usar con el operador de carácter.

**FIN de Específicos de Microsoft**

## <a name="see-also"></a>Vea también

[Operadores de preprocesador](../preprocessor/preprocessor-operators.md)
