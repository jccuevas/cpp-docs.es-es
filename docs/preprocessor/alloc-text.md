---
title: alloc_text
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.alloc_text
- alloc_text_CPP
helpviewer_keywords:
- alloc_text pragma
- pragmas, alloc_text
ms.assetid: 1fd7be18-e4f7-4f70-b079-6326f72b871a
ms.openlocfilehash: 399e8956a511f289b480e66db7f03cac0a6c7c20
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59031370"
---
# <a name="alloctext"></a>alloc_text
Designa la sección de código donde residirán las definiciones de función especificadas. La directiva pragma debe aparecer entre un declarador de función y la definición de función para las funciones designadas.

## <a name="syntax"></a>Sintaxis

```
#pragma alloc_text( "
textsection
", function1, ... )
```

## <a name="remarks"></a>Comentarios

El **alloc_text** pragma no controla funciones miembro de C++ o funciones sobrecargadas. Es aplicable solo a las funciones declaradas con vinculación C, es decir, las funciones declaradas con el **extern "C"** especificación de vinculación. Si intenta utilizar esta directiva pragma en una función con vinculación de C++, se genera un error del compilador.

Ya que el uso del direccionamiento de función `__based` no se admite, especificar ubicaciones de sección requiere el uso de la **alloc_text** pragma. El nombre especificado por *textsection* debe incluirse entre comillas dobles.

El **alloc_text** pragma debe aparecer después de las declaraciones de cualquiera de las funciones especificadas y antes de las definiciones de estas funciones.

Las funciones que se hace referenciadas en un **alloc_text** pragma debe definirse en el mismo módulo que la directiva pragma. Si no es así y después se compila una función sin definir en otra sección de texto, el error se puede detectar o no. Aunque lo normal es que el programa se ejecute correctamente, la función no se asignará en las secciones previstas.

Otra limitación respecto al **alloc_text** son los siguientes:

- No se puede utilizar dentro de una función.

- Debe utilizarse una vez declarada la función, pero antes de que esta se haya definido.

## <a name="see-also"></a>Vea también

[Directives pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)