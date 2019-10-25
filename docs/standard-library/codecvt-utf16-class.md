---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: a84ca6da22825ca3fa7ab43e43a574fb05caa1a8
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72689822"
---
# <a name="codecvt_utf16"></a>codecvt_utf16

Representa una faceta [locale](../standard-library/locale-class.md) que convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y un flujo de bytes codificados como UTF-16LE o UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parámetros

@No__t_1 *Elem*
Tipo de elemento de carácter ancho.

@No__t_1 de *maxcode*
Número máximo de caracteres de la faceta de configuración regional.

@No__t_1 *modo*
Información de configuración de la faceta de configuración regional.

## <a name="remarks"></a>Comentarios

Esta plantilla de clase convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y una secuencia de bytes codificada como UTF-16LE, si el modo & LITTLE_ENDIAN o UTF-16BE en caso contrario.

El flujo de bytes debe escribirse en un archivo binario; puede dañarse si se escribe en un archivo de texto.

## <a name="requirements"></a>Requisitos

Encabezado: \<codecvt >

Espacio de nombres: STD