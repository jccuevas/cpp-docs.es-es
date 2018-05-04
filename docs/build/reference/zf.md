---
title: /ZF (generación con mayor rapidez PDB) | Documentos de Microsoft
ms.date: 03/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /Zf
dev_langs:
- C++
helpviewer_keywords:
- /Zf
- -Zf
author: corob-msft
ms.author: corob
ms.openlocfilehash: 968ce17302fa608888c7ae2fedf695946b0119bd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/03/2018
---
# <a name="zf-faster-pdb-generation"></a>/ZF (generación PDB más rápido)

Habilitar la generación de PDB más rápido en compilaciones en paralelo, pues minimiza las llamadas RPC al mspdbsrv.exe.

## <a name="syntax"></a>Sintaxis

> **/ZF**

## <a name="remarks"></a>Comentarios

El **/Zf** opción habilita la compatibilidad de compilador para la generación más rápida de archivos PDB cuando se usa el [/MP (compilar con varios procesos)](mp-build-with-multiple-processes.md) opción, o cuando el sistema de compilación (por ejemplo, [MSBuild ](/visualstudio/msbuild/msbuild-reference) o [CMake](../../ide/cmake-tools-for-visual-cpp.md)) puede ejecutar cl.exe varios procesos de compilador al mismo tiempo. Esta opción hace que el front-end de compilador retrasar la generación de índices de tipo para cada registro de tipo en el archivo PDB hasta el final de la compilación, a continuación, las solicita todo en una única llamada RPC para mspdbsrv.exe, en lugar de realizar una solicitud RPC para cada registro. Esencialmente, esto puede mejorar el rendimiento de la compilación al reducir la carga RPC sobre el proceso de mspdbsrv.exe en un entorno donde varios procesos de compilador cl.exe ejecutan simultáneamente.

Dado que la **/Zf** opción solo se aplica a la generación de PDB, requiere la [/Zi](z7-zi-zi-debug-information-format.md) o [/Zi](z7-zi-zi-debug-information-format.md) opción.

El **/Zf** opción está disponible a partir de Visual Studio 2017 versión 15,1, donde está desactivada de forma predeterminada. A partir de Visual Studio 2017 versión 15,7 Preview 3, esta opción está de forma predeterminada cuando la **/Zi** o **/Zi** opción está habilitada.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [trabajar con configuraciones de proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C/C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad para incluir **/Zf** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador por orden alfabético](compiler-options-listed-alphabetically.md)<br/>
[/MP (Compilar con varios procesos)](mp-build-with-multiple-processes.md)<br/>
