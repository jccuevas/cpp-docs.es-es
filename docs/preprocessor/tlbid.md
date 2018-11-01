---
title: tlbid
ms.date: 10/18/2018
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 31b71f7c195a7e2ee649b40197551e4ff5efda2c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584523"
---
# <a name="tlbid"></a>tlbid

**Específicos de C++**

Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.

## <a name="syntax"></a>Sintaxis

```
tlbid(number)
```

### <a name="parameters"></a>Parámetros

*Número*<br/>
Número de la biblioteca de tipos en `filename`.

## <a name="remarks"></a>Comentarios

Si se crean varias bibliotecas de tipos en un único archivo DLL, se pueden cargar bibliotecas distintas de la biblioteca de tipos principal mediante el uso de **tlbid**.

Por ejemplo:

```cpp
#import <MyResource.dll> tlbid(2)
```

equivale a:

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)