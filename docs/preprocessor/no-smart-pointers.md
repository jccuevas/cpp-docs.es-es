---
title: no_smart_pointers
ms.date: 11/04/2016
f1_keywords:
- no_search_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: ed4950b9e90ef968fcf0c42e4f0a9775c58ea7ec
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59030172"
---
# <a name="nosmartpointers"></a>no_smart_pointers
**Específicos de C++**

Suprime la creación de punteros inteligentes para todas las interfaces en la biblioteca de tipos.

## <a name="syntax"></a>Sintaxis

```
no_smart_pointers
```

## <a name="remarks"></a>Comentarios

De forma predeterminada, cuando se utiliza `#import`, se obtiene una declaración de puntero inteligente para todas las interfaces de la biblioteca de tipos. Estos punteros inteligentes son de tipo [clase _com_ptr_t](../cpp/com-ptr-t-class.md).

**Específicos de C++: END**

## <a name="see-also"></a>Vea también

[Atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[#import (Directiva)](../preprocessor/hash-import-directive-cpp.md)