---
title: setlocale
ms.date: 11/04/2016
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: b2f28a14b4d4585575a39dd9a936a56a84eeddc4
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59022430"
---
# <a name="setlocale"></a>setlocale

Define la configuración regional (país o región e idioma) que se utilizará al traducir constantes de caracteres y literales de cadena anchos.

## <a name="syntax"></a>Sintaxis

```
#pragma setlocale( "[locale-string]" )
```

## <a name="remarks"></a>Comentarios

Puesto que el algoritmo para convertir caracteres multibyte en caracteres anchos puede variar en función de la configuración regional o la compilación puede tener lugar en una configuración regional diferente de donde se ejecuta un archivo ejecutable, esta directiva pragma proporciona una manera de especificar la configuración regional de destino en tiempo de compilación. Esto garantiza que las cadenas de caracteres anchos se almacenen en el formato correcto.

El valor predeterminado *cadena de configuración regional* es "".

La configuración regional "C" asigna cada carácter de la cadena a su valor como un **wchar_t** (entero corto sin signo). Otros valores que son válidos para `setlocale` son las entradas que se encuentran en el [cadenas de idioma](../c-runtime-library/language-strings.md) lista. Por ejemplo, podría emitir:

```cpp
#pragma setlocale("dutch")
```

La capacidad de emitir una cadena de idioma depende de la compatibilidad con la página de códigos y el identificador de idioma en el equipo.

## <a name="see-also"></a>Vea también

[Directives pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)