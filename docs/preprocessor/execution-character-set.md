---
title: execution_character_set (Pragma)
ms.date: 08/29/2019
f1_keywords:
- execution_character_set
- vc-pragma.execution_character_set
helpviewer_keywords:
- pragma execution_character_set
ms.assetid: 32248cbc-7c92-4dca-8442-230c052b53ad
ms.openlocfilehash: 0c2c812f27634f397af91eace7a41c0e71c1eb99
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70218628"
---
# <a name="execution_character_set-pragma"></a>execution_character_set (Pragma)

Especifica el juego de caracteres de ejecución utilizado para los literales de cadena y carácter. Esta Directiva no es necesaria para los literales marcados `u8` con el prefijo.

## <a name="syntax"></a>Sintaxis

> **#pragma execution_character_set (** "*destino*" **)**

### <a name="parameters"></a>Parámetros

*dirigir*\
Especifica el juego de caracteres de ejecución de destino. Actualmente, el único conjunto de ejecución de destino admitido es "UTF-8".

## <a name="remarks"></a>Comentarios

Esta Directiva del compilador está obsoleta a partir de Visual Studio 2015 Update 2. Se recomienda utilizar `/execution-charset:utf-8` las opciones del compilador o `/utf-8` junto con el `u8` uso del prefijo en los literales de carácter y de cadena estrechos que contienen caracteres extendidos. Para obtener más información sobre `u8` el prefijo, vea literales de [cadena y carácter](../cpp/string-and-character-literals-cpp.md). Para obtener más información sobre las opciones del compilador, vea [/Execution-charset (establecer el juego de caracteres de ejecución)](../build/reference/execution-charset-set-execution-character-set.md) y [/UTF-8 (establecer los juegos de caracteres de origen y de ejecución en UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md).

La `#pragma execution_character_set("utf-8")` Directiva indica al compilador que codifique los literales de cadena estrechos y de caracteres estrechos en el código fuente como UTF-8 en el ejecutable. Esta codificación de salida es independiente de la codificación de archivo de origen utilizada.

De forma predeterminada, el compilador codifica los caracteres estrechos y las cadenas estrechas mediante la página de códigos actual como juego de caracteres de ejecución. Esto significa que los caracteres Unicode o DBCS de un literal que están fuera del intervalo de la página de códigos actual se convierten en el carácter de reemplazo predeterminado en el resultado. Los caracteres Unicode y DBCS se truncan a su byte de orden inferior. Esto es casi seguro que no es lo que pretende. Puede especificar la codificación UTF-8 para literales en el archivo de código fuente mediante un `u8` prefijo. El compilador pasa estas cadenas con codificación UTF-8 a la salida sin cambios. Los literales de caracteres estrechos precedidos por el uso de U8 deben caber en un byte, o bien se truncan en la salida.

De forma predeterminada, Visual Studio usa la página de códigos actual como el juego de caracteres de origen que se usa para interpretar el código fuente para la salida. Cuando se lee un archivo en, Visual Studio lo interpreta según la página de códigos actual a menos que se haya establecido la página de códigos del archivo, o a menos que se detecten una marca de orden de bytes (BOM) o caracteres UTF-16 al principio del archivo. Dado que UTF-8 no se puede establecer como la página de códigos actual, cuando la detección automática encuentra archivos de origen codificados como UTF-8 sin una marca BOM, Visual Studio supone que están codificados mediante la página de códigos actual. Los caracteres del archivo de código fuente que están fuera del intervalo de la página de códigos especificada o detectada automáticamente pueden producir errores y advertencias del compilador.

## <a name="see-also"></a>Vea también

[Directivas pragma y la \_ \_palabra clave pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)\
[/Execution-charset (establecer juego de caracteres de ejecución)](../build/reference/execution-charset-set-execution-character-set.md)\
[/utf-8 (Establecer los juegos de caracteres de ejecución y origen en UTF-8)](../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)
