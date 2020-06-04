---
title: wbuffer_convert (Clase)
ms.date: 11/04/2016
f1_keywords:
- xlocmon/stdext::cvt::wbuffer_convert
helpviewer_keywords:
- wbuffer_convert class
ms.assetid: 4a56f9bf-4138-4612-b516-525fea401358
ms.openlocfilehash: 8de0091af93120290105ce7603fae5acff257b76
ms.sourcegitcommit: 590e488e51389066a4da4aa06d32d4c362c23393
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/21/2019
ms.locfileid: "72688541"
---
# <a name="wbuffer_convert-class"></a>wbuffer_convert (Clase)

Describe un búfer de secuencia que controla la transmisión de elementos a y desde un búfer de secuencia de bytes.

## <a name="syntax"></a>Sintaxis

```cpp
template <class Codecvt, class Elem = wchar_t, class Traits = std::char_traits<Elem>>
class wbuffer_convert
    : public std::basic_streambuf<Elem, Traits>
```

### <a name="parameters"></a>Parámetros

|Parámetro|Descripción|
|---------------|-----------------|
|*Codecvt*|La faceta [locale](../standard-library/locale-class.md) que representa el objeto de conversión.|
|*Elem*|Tipo de elemento de carácter ancho.|
|*Rasgos*|Los rasgos asociados a *Elem*.|

## <a name="remarks"></a>Comentarios

Esta plantilla de clase describe un búfer de secuencia que controla la transmisión de elementos de tipo `_Elem`, cuyos rasgos de caracteres se describen en la clase `Traits`, hacia y desde un búfer de secuencia de bytes de tipo `std::streambuf`.

La conversión entre una secuencia de valores `Elem` y las secuencias multibyte se realiza con un objeto de clase `Codecvt<Elem, char, std::mbstate_t>`, que cumple los requisitos de la faceta de conversión de código estándar `std::codecvt<Elem, char, std::mbstate_t>`.

Un objeto de esta plantilla de clase almacena:

- Un puntero a su búfer de secuencia de bytes subyacente

- Un puntero al objeto de conversión asignado (que se libera cuando el [wbuffer_convert](../standard-library/wbuffer-convert-class.md)
