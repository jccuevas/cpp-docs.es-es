---
title: /ZF (generación de PDB más rápida)
ms.date: 03/29/2018
f1_keywords:
- /Zf
helpviewer_keywords:
- /Zf
- -Zf
ms.openlocfilehash: bed37a189e3eb1eb7b55dbdee1f81f360eafa721
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57814051"
---
# <a name="zf-faster-pdb-generation"></a>/ZF (generación de PDB más rápida)

Habilitar generación de PDB más rápida en las compilaciones en paralelo, ya que minimiza las llamadas RPC a mspdbsrv.exe.

## <a name="syntax"></a>Sintaxis

> **/Zf**

## <a name="remarks"></a>Comentarios

El **/Zf** opción habilita la compatibilidad de compilador para la generación más rápida de archivos PDB cuando se usa el [/MP (compilar con varios procesos)](mp-build-with-multiple-processes.md) opción, o cuando el sistema de compilación (por ejemplo, [MSBuild ](/visualstudio/msbuild/msbuild-reference) o [CMake](../cmake-projects-in-visual-studio.md)) puede ejecutar cl.exe varios procesos de compilador al mismo tiempo. Esta opción hace que el front-end de compilador retrasar la generación de índices de tipos para cada registro de tipo en el archivo PDB hasta el final de la compilación, a continuación, se les solicita todo en una sola llamada RPC a mspdbsrv.exe, en lugar de realizar una solicitud RPC para cada registro. Esto puede mejorar considerablemente el rendimiento de la compilación al reducir la carga RPC en el proceso de mspdbsrv.exe en un entorno donde se ejecutan simultáneamente varios procesos de compilador cl.exe.

Dado que el **/Zf** opción solo se aplica a la generación de PDB, requiere el [/Zi](z7-zi-zi-debug-information-format.md) o [/Zi](z7-zi-zi-debug-information-format.md) opción.

El **/Zf** opción está disponible a partir de Visual Studio 2017 versión 15.1, donde está desactivada de forma predeterminada. A partir de Visual Studio 2017 versión 15.7 Preview 3, esta opción está activada de forma predeterminada cuando la **/Zi** o **/Zi** está habilitada.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir **/Zf** y, a continuación, elija **Aceptar**.

## <a name="see-also"></a>Vea también

[Opciones del compilador por orden alfabético](compiler-options-listed-alphabetically.md)<br/>
[/MP (Compilar con varios procesos)](mp-build-with-multiple-processes.md)<br/>
