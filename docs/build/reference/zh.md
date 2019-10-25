---
title: /ZH (algoritmo hash para el cálculo de la suma de comprobación de archivo en la información de depuración)
description: Use la opción del compilador/ZH para habilitar sumas de comprobación de archivos de código fuente MD5, SHA-1 o SHA-256 en información de depuración
ms.date: 09/16/2019
f1_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
helpviewer_keywords:
- /ZH
- /ZH:MD5
- /ZH:SHA1
- /ZH:SHA_256
- /ZH compiler option
- /ZH:MD5 compiler option
- /ZH:SHA1 compiler option
- /ZH:SHA_256 compiler option
- Hash algorithm for file checksum in debug info
ms.openlocfilehash: f05dc2bc3b8ce4502ff16a6e19fdbb10763b34ba
ms.sourcegitcommit: 1e6386be9084f70def7b3b8b4bab319a117102b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/30/2019
ms.locfileid: "71686939"
---
# <a name="zh-hash-algorithm-for-calculation-of-file-checksum-in-debug-info"></a>/ZH (algoritmo hash para el cálculo de la suma de comprobación de archivo en la información de depuración)

Especifica el algoritmo hash criptográfico que se va a utilizar para generar una suma de comprobación de cada archivo de código fuente.

## <a name="syntax"></a>Sintaxis

> **/ZH:** {**MD5**|**SHA1**|**SHA_256**}

## <a name="arguments"></a>Argumentos

**/ZH: MD5**\
Use un hash MD5 para la suma de comprobación. Esta opción es la predeterminada.

**/ZH: SHA1**\
Use un hash SHA-1 para la suma de comprobación.

**/ZH: SHA_256**\
Use un hash SHA-256 para la suma de comprobación.

## <a name="remarks"></a>Comentarios

Los archivos PDB almacenan una suma de comprobación para cada archivo de código fuente compilado en el código objeto del archivo ejecutable asociado. La suma de comprobación permite al depurador comprobar que el código fuente que se carga coincide con el archivo ejecutable. El compilador y el depurador admiten algoritmos hash MD5, SHA-1 y SHA-256. De forma predeterminada, el compilador utiliza un hash MD5 para generar la suma de comprobación. Puede especificar esta opción explícitamente mediante la opción **/ZH: MD5** .

Debido a un riesgo de problemas de colisión en MD5 y SHA-1, Microsoft recomienda usar la opción **/ZH: SHA_256** . El hash SHA-256 puede dar lugar a un pequeño aumento en los tiempos de compilación.

Cuando se especifica más de una opción **/ZH** , se usa la última opción.

La opción **/ZH** está disponible a partir de la versión 16,4 de Visual Studio 2019.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Establezca la lista desplegable **configuración** en **todas las configuraciones**.

1. Seleccione la página de propiedades **Propiedades de configuración** > **C/C++**  > **Línea de comandos**.

1. Modifique la **propiedad opciones adicionales** para agregar una **opción/ZH: MD5**, **/ZH: SHA1**o **/ZH: SHA_256** y, después, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del Compilador](compiler-options.md)\
[Servidor de origen](/windows/win32/debug/source-server-and-source-indexing)
