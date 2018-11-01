---
title: no_smart_pointers
ms.date: 11/04/2016
f1_keywords:
- no_search_pointers
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
ms.openlocfilehash: 305c08497a600f602767496cba48d108335fdeb8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50636987"
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

**FIN de específicos de C++**

## <a name="see-also"></a>Vea también

[atributos #import](../preprocessor/hash-import-attributes-cpp.md)<br/>
[directiva #import](../preprocessor/hash-import-directive-cpp.md)