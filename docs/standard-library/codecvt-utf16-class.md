---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: 73177985727f4da5cf3ca4eb9e3cc3fb5976f76d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215285"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

Representa una faceta [locale](../standard-library/locale-class.md) que convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y un flujo de bytes codificados como UTF-16LE o UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parámetros

\ *Elem*
Tipo de elemento de carácter ancho.

\ de *maxcode*
Número máximo de caracteres de la faceta de configuración regional.

\ *modo*
Información de configuración de la faceta de configuración regional.

## <a name="remarks"></a>Observaciones

Esta plantilla de clase convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y una secuencia de bytes codificada como UTF-16LE, si el modo & little_endian o UTF-16BE en caso contrario.

El flujo de bytes debe escribirse en un archivo binario; puede dañarse si se escribe en un archivo de texto.

## <a name="requirements"></a>Requisitos

Encabezado: \<codecvt >

Espacio de nombres: std
