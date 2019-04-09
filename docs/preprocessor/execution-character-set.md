---
title: execution_character_set
ms.date: 10/18/2018
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: bd31e8e91a1bcbfa6ace9b47fa2b13dd945adb20
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59039931"
---
# <a name="executioncharacterset"></a>execution_character_set

Especifica el juego de caracteres de ejecución utilizado para literales de cadena y carácter. Esta directiva no es necesaria para los literales de marcado con el prefijo u8.

## <a name="syntax"></a>Sintaxis

```
#pragma execution_character_set("target")
```

### <a name="parameters"></a>Parámetros

*target*<br/>
Especifica el juego de caracteres de ejecución de destino. Actualmente la ejecución de destino solo establecer compatible es "utf-8".

## <a name="remarks"></a>Comentarios

Esta directiva de compilador es obsoleta a partir de Visual Studio 2015 Update 2. Se recomienda que use el `/execution-charset:utf-8` o `/utf-8` opciones del compilador junto con utilizando el `u8` prefijo en literales de caracteres y cadenas estrechos que contienen caracteres extendidos. Para obtener más información sobre la `u8` prefix, consulte [literales de cadena y carácter](../cpp/string-and-character-literals-cpp.md). Para obtener más información acerca de las opciones del compilador, vea [/Execution-CharSet (establecer juego de caracteres de ejecución)](../build/reference/execution-charset-set-execution-character-set.md) y [/UTF-8 (establecer origen y ejecutable juegos a UTF-8 de caracteres)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).

El `#pragma execution_character_set("utf-8")` directiva indica al compilador para codificar caracteres estrechos y literales de cadena estrechos en el código fuente como UTF-8 en el archivo ejecutable. Esta codificación de salida es independiente de la codificación de archivo de origen utilizada.

De forma predeterminada, el compilador codifica caracteres estrechos y cadenas de caracteres estrechos mediante el uso de la página de códigos actual como el juego de caracteres de ejecución. Esto significa que los caracteres Unicode o DBCS en un literal que están fuera del intervalo de la página de códigos actual se convierten en el carácter de reemplazo predeterminado en la salida. Se truncan los caracteres Unicode y DBCS en su byte de orden inferior. Esto es casi seguro que no lo que piensa. Puede especificar la codificación UTF-8 para los literales en el archivo de origen mediante el uso de un `u8` prefijo. El compilador pasa estas cadenas con codificación UTF-8 a la salida sin cambios. Literales de caracteres estrechos mediante el uso de u8 el prefijo deben caber en un byte, o que se trunquen en la salida.

De forma predeterminada, Visual Studio usa la página de códigos actual como el juego de caracteres de origen utilizado para interpretar el código fuente para la salida. Cuando se lee un archivo en, Visual Studio lo interpreta según la página de códigos actual a menos que se estableció la página de códigos del archivo, o una marca de orden de bytes (BOM) o caracteres de UTF-16 se detectan al principio del archivo. Dado que UTF-8 no se puede establecer como página de códigos actual, cuando encuentra la detección automática con archivos de código fuente codificados como UTF-8 sin una marca BOM, Visual Studio se da por supuesto que se codifican mediante el uso de la página de códigos actual. Caracteres en el archivo de origen que se encuentra fuera del intervalo especificado o automáticamente detectan página de códigos puede provocar errores y advertencias del compilador.

## <a name="see-also"></a>Vea también

[Directivas pragma y la \_ \_Pragma (palabra clave)](../preprocessor/pragma-directives-and-the-pragma-keyword.md)<br/>
[/ Execution-CharSet (establecer juego de caracteres de ejecución)](../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/ UTF-8 (establecer origen y el ejecutable juegos de caracteres en UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)