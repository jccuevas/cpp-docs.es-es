---
title: '@ (Especificar un archivo de respuesta del compilador)'
ms.date: 11/04/2016
f1_keywords:
- '@'
helpviewer_keywords:
- response files, C/C++ compiler
- '@ compiler option'
- cl.exe compiler, specifying response files
ms.assetid: 400fffee-909d-4f60-bf76-45833e822685
ms.openlocfilehash: c2b5578e1ce1db590bdf5abbff0c91e858803ad7
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62273007"
---
# <a name="-specify-a-compiler-response-file"></a>@ (Especificar un archivo de respuesta del compilador)

Especifica un archivo de respuesta del compilador.

## <a name="syntax"></a>Sintaxis

> **\@**<em>response_file</em>

## <a name="arguments"></a>Argumentos

*response_file*<br/>
Un archivo de texto que contiene comandos del compilador.

## <a name="remarks"></a>Comentarios

Un archivo de respuesta puede contener cualquier comando que debe especificar en la línea de comandos. Esto puede ser útil si los argumentos de línea de comandos supera los 127 caracteres.

No es posible especificar el **\@** opción desde dentro de un archivo de respuesta. Es decir, un archivo de respuesta no puede incrustar otro archivo de respuesta.

Desde la línea de comandos puede especificar tantas opciones de archivo de respuesta (por ejemplo, `@respfile.1 @respfile.2`) como desee.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

- Un archivo de respuesta no se pueden especificar desde el entorno de desarrollo y debe especificarse en la línea de comandos.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- No se puede cambiar esta opción del compilador mediante programación.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
