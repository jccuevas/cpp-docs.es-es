---
title: /Zo (Mejorar la depuración optimizada)
ms.date: 11/04/2016
f1_keywords:
- -Zo
- /Zo
helpviewer_keywords:
- Zo compiler option [C++]
- /Zo compiler option [C++]
- -Zo compiler option [C++]
ms.assetid: eea8d89a-7fe0-4fe1-86b2-7689bbebbd7f
ms.openlocfilehash: 2fb64b0cc39d5b7ff0c96d3eae47197c455526f5
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809943"
---
# <a name="zo-enhance-optimized-debugging"></a>/Zo (Mejorar la depuración optimizada)

Genera información de depuración mejorada para código optimizado en versiones no depuradas.

## <a name="syntax"></a>Sintaxis

```cpp
/Zo[-]
```

## <a name="remarks"></a>Comentarios

El **/Zo** modificador del compilador genera información de depuración mejorada para código optimizado. La optimización puede usar registros para variables locales, reordenar código, vectorizar bucles y llamadas a funciones en línea. Estas optimizaciones pueden interferir con la relación entre el código fuente y el código de objeto compilado. El **/Zo** modificador indica al compilador que genere información de depuración adicional para variables locales y las funciones insertadas. Úselo para ver las variables en el **automático**, **variables locales**, y **inspección** optimizado de windows cuando se recorra el código en el depurador de Visual Studio. También permite que los seguimientos de pila muestren las funciones inline en el depurador WinDBG. Las compilaciones que se han deshabilitado las optimizaciones de depuración ([/Od](od-disable-debug.md)) no necesita la información de depuración adicional generada cuando **/Zo** se especifica. Use la **/Zo** conmutador para configuraciones de la versión de depuración con la optimización activada. Para obtener más información sobre los modificadores de optimización, vea [opciones /O (optimizar código)](o-options-optimize-code.md). El **/Zo** opción está habilitada de forma predeterminada en Visual Studio cuando se especifica la información de depuración con **/Zi** o **/Z7**. Especificar **/Zo-** para deshabilitar explícitamente esta opción del compilador.

El **/Zo** conmutador está disponible a partir de Visual Studio 2013 Update 3 y reemplaza el no documentado anteriormente **/d2Zi+** cambie.

### <a name="to-set-the-zo-compiler-option-in-visual-studio"></a>Para establecer la opción del compilador /Zo en Visual Studio

1. Abra el **páginas de propiedades** cuadro de diálogo para el proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **propiedades de configuración**, **C o C++** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Modificar el **opciones adicionales** propiedad incluir `/Zo` y, a continuación, elija **Aceptar**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[/O (Opciones) (Optimizar código)](o-options-optimize-code.md)<br/>
[/Z7, /Zi, /ZI (Formato de la información de depuración)](z7-zi-zi-debug-information-format.md)<br/>
[Editar y continuar](/visualstudio/debugger/edit-and-continue)
