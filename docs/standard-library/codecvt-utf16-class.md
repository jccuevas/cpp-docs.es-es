---
title: codecvt_utf16
ms.date: 11/04/2016
f1_keywords:
- codecvt/std::codecvt_utf16
helpviewer_keywords:
- codecvt_utf16 class
ms.assetid: a9897f98-f84d-4db6-90ad-858b2727570c
ms.openlocfilehash: 18b95884bb673305398739968ef2530e8c4778d1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62405227"
---
# <a name="codecvtutf16"></a>codecvt_utf16

Representa una faceta [locale](../standard-library/locale-class.md) que convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y un flujo de bytes codificados como UTF-16LE o UTF-16BE.

```cpp
template<class Elem, unsigned long Maxcode = 0x10ffff, codecvt_mode Mode = (codecvt_mode)0>
class codecvt_utf16 : public std::codecvt<Elem, char, StateType>
```

## <a name="parameters"></a>Parámetros

*Elem*<br/>
Tipo de elemento de carácter ancho.

*Maxcode*<br/>
Número máximo de caracteres de la faceta de configuración regional.

*Modo*<br/>
Información de configuración de la faceta de configuración regional.

## <a name="remarks"></a>Comentarios

Esta clase de plantilla convierte entre caracteres anchos codificados como UCS-2 o UCS-4 y un flujo de bytes codificados como UTF-16LE, si Mode & little_endian, o UTF-16BE en caso contrario.

El flujo de bytes debe escribirse en un archivo binario; puede dañarse si se escribe en un archivo de texto.

## <a name="requirements"></a>Requisitos

Encabezado: \<codecvt >

Namespace: std