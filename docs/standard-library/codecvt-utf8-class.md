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
ms.openlocfilehash: 9c0230c92a448eedf0cae7c80778c2bd4c48d077
ms.sourcegitcommit: 3614b52b28c24f70d90b20d781d548ef74ef7082
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 07/11/2018
ms.locfileid: "38963172"
---
# <a name="codecvtutf8"></a>codecvt_utf8

Representa una faceta de [configuración regional](../standard-library/locale-class.md) que convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y un flujo de bytes codificados como UTF-8.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf8 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parámetros

*Elem* el tipo de elemento de caracteres anchos.
*Maxcode* el número máximo de caracteres para la faceta de configuración regional.
*Modo* información de configuración de la faceta de configuración regional.

## <a name="remarks"></a>Comentarios

El flujo de bytes puede escribirse en un archivo binario o en un archivo de texto.

## <a name="requirements"></a>Requisitos

Encabezado: Espacio de nombres <codecvt>: std
