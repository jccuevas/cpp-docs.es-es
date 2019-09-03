---
title: atributo de importación TLBID
ms.date: 08/29/2019
f1_keywords:
- tlbid
helpviewer_keywords:
- tlbid attribute
ms.assetid: 54b06785-191b-4e77-a9a5-485f2b4acb09
ms.openlocfilehash: 364fb224b0f2769cb0933e71d18ff70768189328
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70216541"
---
# <a name="tlbid-import-attribute"></a>atributo de importación TLBID

**C++Cuestión**

Permite cargar bibliotecas distintas de la biblioteca de tipos primaria.

## <a name="syntax"></a>Sintaxis

> **#import** *biblioteca de tipos-dll* **TLBID (** *número* **)**

### <a name="parameters"></a>Parámetros

*números*\
El número de la biblioteca de tipos en el *archivo de biblioteca de tipos*.

## <a name="remarks"></a>Comentarios

Si hay varias bibliotecas de tipos integradas en un único archivo DLL, es posible cargar bibliotecas distintas de la biblioteca de tipos principal mediante **TLBID**.

Por ejemplo:

```cpp
#import <MyResource.dll> tlbid(2)
```

equivale a:

```cpp
LoadTypeLib("MyResource.dll\\2");
```

**Específico C++ de finalización**

## <a name="see-also"></a>Vea también

[atributos de #import](../preprocessor/hash-import-attributes-cpp.md)\
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)
