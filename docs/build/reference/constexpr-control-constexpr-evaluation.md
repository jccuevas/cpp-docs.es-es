---
title: /constexpr (Controlar la evaluación constexpr)
ms.date: 08/15/2017
f1_keywords:
- /constexpr
- -constexpr
helpviewer_keywords:
- /constexpr control constexpr evaluation [C++]
- -constexpr control constexpr evaluation [C++]
- constexpr control constexpr evaluation [C++]
ms.assetid: 76d56784-f5ad-401d-841d-09d1059e8b8c
ms.openlocfilehash: 4d3f33a64dcebfc40778f81354cb5067a5239ace
ms.sourcegitcommit: 6b749db14b4cf3a2b8d581fda6fdd8cb98bc3207
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/05/2020
ms.locfileid: "82825596"
---
# <a name="constexpr-control-constexpr-evaluation"></a>/constexpr (Controlar la evaluación constexpr)

Use las opciones del compilador **/constexpr** para controlar los parámetros para la evaluación de **constexpr** en tiempo de compilación.

## <a name="syntax"></a>Sintaxis

> **/constexpr: profundidad**<em>N</em>\
> **/constexpr: subseguimiento**<em>N</em>\
> **/constexpr: pasos**<em>N</em>

## <a name="arguments"></a>Argumentos

**profundidad**<em>n</em> limite la profundidad de la invocación recursiva de funciones **constexpr** a *N* niveles. El valor predeterminado es 512.

el **seguimiento**de la copia de seguridad<em>n</em> muestra hasta *n* evaluaciones de **constexpr** en diagnósticos. El valor predeterminado es 10.

**pasos**<em>n</em> finalizar la evaluación de **constexpr** después de *N* pasos. El valor predeterminado es 100.000.

## <a name="remarks"></a>Observaciones

Las opciones del compilador **/constexpr** controlan la evaluación en tiempo de compilación de las expresiones **constexpr** . Los pasos de evaluación, los niveles de recursividad y la profundidad del seguimiento se controlan para evitar que el compilador no gastar demasiado tiempo en la evaluación de **constexpr** . Para obtener más información sobre el elemento de lenguaje **constexpr** , vea [constexpr (C++)](../../cpp/constexpr-cpp.md).

Las opciones de **/constexpr** están disponibles a partir de Visual Studio 2015.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **páginas de propiedades** del proyecto.

2. En **propiedades de configuración**, expanda la carpeta **C/C++** y elija la página de propiedades **línea de comandos** .

3. Escriba cualquier opción del compilador de **/constexpr** en el cuadro **opciones adicionales** . Elija **Aceptar** o **aplicar** para guardar los cambios.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Consulte también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
