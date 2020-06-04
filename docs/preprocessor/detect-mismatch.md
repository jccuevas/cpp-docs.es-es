---
title: detect_mismatch (Pragma)
ms.date: 08/29/2019
f1_keywords:
- vc-pragma.detect_mismatch
- detect_mismatch_CPP
helpviewer_keywords:
- pragmas, detect_mismatch
- detect_mismatch pragma
ms.assetid: ddb13ac9-0e2f-40ce-be69-7e44c04f5a12
ms.openlocfilehash: 6e247b3f251bce47710a3380fb295597314a3bd8
ms.sourcegitcommit: 6e1c1822e7bcf3d2ef23eb8fac6465f88743facf
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/03/2019
ms.locfileid: "70222394"
---
# <a name="detect_mismatch-pragma"></a>detect_mismatch (Pragma)

Inserta un registro en un objeto. El vinculador comprueba estos registros para detectar potenciales discordancias.

## <a name="syntax"></a>Sintaxis

> **#pragma detect_mismatch (** "*Name*" **,** "*Value*" **)**

## <a name="remarks"></a>Comentarios

Al vincular el proyecto, el vinculador produce un error [LNK2038](../error-messages/tool-errors/linker-tools-error-lnk2038.md) si el proyecto contiene dos objetos con el mismo *nombre* pero cada uno tiene un *valor*diferente. Utilice esta directiva pragma para evitar la vinculación de archivos objeto incoherentes.

*El nombre y el* *valor* son literales de cadena y obedecen las reglas para los literales de cadena con respecto a los caracteres de escape y la concatenación. Distinguen mayúsculas de minúsculas y no pueden contener una coma, el signo igual, las comillas o el carácter **nulo** .

## <a name="example"></a>Ejemplo

En este ejemplo se crean dos archivos que tienen números de versión diferentes para la misma etiqueta de versión.

```cpp
// pragma_directive_detect_mismatch_a.cpp
#pragma detect_mismatch("myLib_version", "9")
int main ()
{
   return 0;
}

// pragma_directive_detect_mismatch_b.cpp
#pragma detect_mismatch("myLib_version", "1")
```

Si compila ambos archivos mediante la línea de comandos `cl pragma_directive_detect_mismatch_a.cpp pragma_directive_detect_mismatch_b.cpp`, recibirá el error `LNK2038`.

## <a name="see-also"></a>Vea también

[Directivas pragma y la palabra clave __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
