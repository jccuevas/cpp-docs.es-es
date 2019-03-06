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
ms.openlocfilehash: c8e9f2b6bc36d8a1dfdada00bca1c7a4dcf65256
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423266"
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

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)
