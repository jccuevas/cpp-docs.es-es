---
title: vector&lt;bool&gt;::reference::operator bool | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- operatorbool
- vector<bool>::reference::operatorbool
- bool
- std::vector<bool>::reference::operatorbool
dev_langs:
- C++
helpviewer_keywords:
- BOOL operator
- reference::operator bool
ms.assetid: b0e57869-18cc-4296-9061-da502f30120d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 00ccd9e9ffbab78534c5b6417b7567ba03d007ab
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963685"
---
# <a name="vectorltboolgtreferenceoperator-bool"></a>vector&lt;bool&gt;::reference::operator bool

Proporciona una conversión implícita de `vector<bool>::reference` a **bool**.

## <a name="syntax"></a>Sintaxis

```cpp
operator bool() const;
```

## <a name="return-value"></a>Valor devuelto

El valor booleano del elemento del objeto [vector\<bool>](../standard-library/vector-bool-class.md).

## <a name="remarks"></a>Comentarios

Este operador no puede modificar el objeto `vector<bool>`.

## <a name="requirements"></a>Requisitos

**Encabezado:** \<vector>

**Espacio de nombres:** std

## <a name="see-also"></a>Vea también

[vector\<bool >:: hacen referencia a clase](../standard-library/vector-bool-reference-class.md)<br/>
[Referencia de biblioteca estándar de C++](../standard-library/cpp-standard-library-reference.md)<br/>
