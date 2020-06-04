---
title: setlocale (Pragma)
ms.date: 08/29/2019
f1_keywords:
- setlocale_CPP
- vc-pragma.setlocale
helpviewer_keywords:
- pragmas, setlocale
- setlocale pragma
ms.assetid: e60b43d9-fbdf-4c4e-ac85-805523a13b86
ms.openlocfilehash: 219354595e5c63b2f13211d43bfa517d97413251
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218179"
---
# <a name="setlocale-pragma"></a>setlocale (Pragma)

Define la *configuración regional*, el país, la región y el idioma que se van a usar al traducir constantes de caracteres anchos y literales de cadena.

## <a name="syntax"></a>Sintaxis

> **#pragma setlocale ("** [ *locale-String* ] **")**

## <a name="remarks"></a>Comentarios

Dado que el algoritmo para convertir los caracteres multibyte en caracteres anchos puede variar según la configuración regional, o la compilación puede tener lugar en una configuración regional diferente de donde se ejecutará un archivo ejecutable, esta pragma proporciona una manera de especificar la configuración regional de destino en tiempo de compilación. Garantiza que las cadenas de caracteres anchos se almacenan en el formato correcto.

La *cadena de configuración regional* predeterminada es "".

La configuración regional "C" asigna cada carácter de la cadena a su valor como **wchar_t**. Otros valores válidos `setlocale` para son las entradas que se encuentran en la lista de [cadenas de idioma](../c-runtime-library/language-strings.md) . Por ejemplo, puede especificar:

```cpp
#pragma setlocale("dutch")
```

La capacidad de especificar una cadena de idioma depende de la compatibilidad de la página de códigos y el ID. de idioma en el equipo.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
