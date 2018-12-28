---
title: /homeparams (Copiar los parámetros del Registro en la pila)
ms.date: 12/17/2018
f1_keywords:
- /homeparams
helpviewer_keywords:
- /homeparams compiler option [C++]
- -homeparams compiler option [C++]
ms.assetid: 51067de4-24f7-436b-b8d9-bc867a7d53aa
ms.openlocfilehash: ffb5ca602feb7a369bb31d0277834786d66ac12a
ms.sourcegitcommit: ff3cbe4235b6c316edcc7677f79f70c3e784ad76
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/19/2018
ms.locfileid: "53627484"
---
# <a name="homeparams-copy-register-parameters-to-stack"></a>/homeparams (Copiar los parámetros del Registro en la pila)

Parámetros de fuerzas pasan en registros también se pueden escribir en sus ubicaciones en la pila de entrada de función.

## <a name="syntax"></a>Sintaxis

> **/homeparams**

## <a name="remarks"></a>Comentarios

Esta opción del compilador sólo está disponible en los compiladores cruzados que tienen como destino x64 y nativo.

La convención de llamada de x64 requiere espacio de pila para que se va a asignar para todos los parámetros, incluso para los parámetros pasados en registros. Para obtener más información, consulte [pasando el parámetro](../../build/x64-calling-convention.md#parameter-passing). De forma predeterminada, los parámetros de registro no se copian en el espacio de pila asignado para ellos en las compilaciones de versión. Esto dificulta la depuración de una generación de versión optimizada del programa.

Para las compilaciones de versión, puede usar el **/homeparams** opción para forzar al compilador para copiar registro parámetros a la pila, para asegurarse de que puede depurar la aplicación. **/homeparams** implica una desventaja de rendimiento, porque requiere un ciclo adicional para cargar los parámetros de registro en la pila.

En las compilaciones de depuración, la pila siempre se rellena con los parámetros pasados en registros.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Abra el **propiedades de configuración** > **C o C++** > **línea de comandos** página de propiedades.

1. Especifique la opción del compilador en el **opciones adicionales** cuadro.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)