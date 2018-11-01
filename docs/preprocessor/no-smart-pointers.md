---
title: no_smart_pointers | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- no_search_pointers
dev_langs:
- C++
helpviewer_keywords:
- no_smart_pointers attribute
ms.assetid: d69dd71e-08a8-4446-a3d0-a062dc29cb17
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 233e302d4035801e7d8871754d8ecfcfee54cf1a
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50060916"
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