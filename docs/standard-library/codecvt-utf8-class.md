---
title: codecvt_utf8 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: reference
f1_keywords:
- codecvt/std::codecvt_utf8
dev_langs:
- C++
helpviewer_keywords:
- codecvt_utf8 class
ms.assetid: 2a87478f-e2d4-4b8d-ad9c-00add01d1bb0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cb5003c94793bc3b8195ebad48b438786b85ce84
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/07/2018
ms.locfileid: "33844047"
---
# <a name="codecvtutf8"></a>codecvt_utf8

Representa una faceta de [configuración regional](../standard-library/locale-class.md) que convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y un flujo de bytes codificados como UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parámetros

`Elem` El tipo de elemento de caracteres anchos.
`Maxcode` El número máximo de caracteres para la faceta de configuración regional.
`Mode` Información de configuración para la faceta de configuración regional.

## <a name="remarks"></a>Comentarios

El flujo de bytes puede escribirse en un archivo binario o en un archivo de texto.

## <a name="requirements"></a>Requisitos

Encabezado: Espacio de nombres <codecvt>: std
