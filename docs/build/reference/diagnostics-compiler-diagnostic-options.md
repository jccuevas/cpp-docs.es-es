---
title: /Diagnostics (opciones del compilador de diagnóstico)
ms.date: 11/11/2016
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
ms.openlocfilehash: 6b7d043e00204fa191530f03bbed069d71a25fc5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293828"
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/Diagnostics (opciones del compilador de diagnóstico)

Use la **/diagnostics** opción del compilador para especificar la visualización de información de ubicación del error y advertencia.

## <a name="syntax"></a>Sintaxis

```
/diagnostics:{caret|classic|column}
```

## <a name="remarks"></a>Comentarios

Esta opción se admite en Visual Studio 2017 y versiones posteriores.

El **/diagnostics** opción del compilador controla la presentación de información de advertencia y error.

El **/diagnostics:classic** es la opción predeterminada, que notifica solo el número de línea donde se encontró el problema.

El **/diagnostics:column** opción también incluye la columna que se ha detectado el problema. Esto puede ayudarle a identificar la construcción de lenguaje específico o el carácter que está causando el problema.

El **/diagnostics:caret** opción incluye la columna donde el problema se ha encontrado y coloca un símbolo de intercalación (^) en la ubicación en la línea de código donde se detectó el problema.

Tenga en cuenta que en algunos casos, el compilador no detecta un problema donde se produjo. Por ejemplo, un punto y coma faltante podrían no detectarse hasta que se han detectado los símbolos de otros, inesperados. La columna se notifica y se coloca el símbolo de intercalación donde el compilador detectó que algo iba mal, que no siempre es donde tiene que realizar la corrección.

El **/diagnostics** opción está disponible a partir de Visual Studio 2017.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el proyecto **páginas de propiedades** cuadro de diálogo.

1. En **propiedades de configuración**, expanda el **C o C++** carpeta y elija el **General** página de propiedades.

1. Use el control de lista desplegable en el **diagnósticos formato** opción de presentación del campo para seleccionar un diagnóstico. Elija **Aceptar** o **aplicar** para guardar los cambios.

## <a name="see-also"></a>Vea también

[Opciones del compilador de MSVC](compiler-options.md)<br/>
[Sintaxis de la línea de comandos del compilador MSVC](compiler-command-line-syntax.md)
