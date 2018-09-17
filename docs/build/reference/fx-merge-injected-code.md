---
title: -Fx (combinar código insertado) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.ExpandAttributedSource
- /Fx
- VC.Project.VCCLCompilerTool.ExpandAttributedSource
dev_langs:
- C++
helpviewer_keywords:
- Fx compiler option [C++]
- -Fx compiler option [C++]
- injected code
- merging injected code
- /Fx compiler option [C++]
ms.assetid: 14f0e301-3bab-45a3-bbdf-e7ce66f20560
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0bd95ea00a63f28f04874f873cf0a4e991fac0fc
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45710526"
---
# <a name="fx-merge-injected-code"></a>/Fx (Combinar código insertado)

Genera una copia de cada archivo de origen con código insertado combinado en el origen.

## <a name="syntax"></a>Sintaxis

```
/Fx
```

## <a name="remarks"></a>Comentarios

Para distinguir un archivo de origen combinado de un archivo de origen original, **/Fx** agrega una extensión .mrg entre el nombre de archivo y la extensión de archivo. Por ejemplo, un archivo denominado MyCode.cpp que contiene código con atributos creado con **/Fx** crea un archivo denominado MyCode.mrg.cpp que contiene el código siguiente:

```
//+++ Start Injected Code
[no_injected_text(true)];      // Suppress injected text, it has
                               // already been injected
#pragma warning(disable: 4543) // Suppress warnings about skipping
                               // injected text
#pragma warning(disable: 4199) // Suppress warnings from attribute
                               // providers
//--- End Injected Code
```

En un archivo .mrg, el código insertado a causa de un atributo se delimita de la siguiente manera:

```
//+++ Start Injected Code
...
//--- End Injected Code
```

El atributo [no_injected_text](../../windows/no-injected-text.md) está insertado en un archivo .mrg, lo que permite la compilación del archivo .mrg sin volver a insertar texto.

Debe tener en cuenta que el archivo de origen .mrg está diseñado para ser una representación del código fuente insertado por el compilador. Es posible que el archivo .mrg no se compile ni ejecute exactamente como el archivo de origen.

Las macros no se expanden en el archivo .mrg.

Si el programa incluye un archivo de encabezado que usa código insertado, **/Fx** genera un archivo .mrg.h para ese encabezado. **/Fx** no combina archivos incluidos que no usan código insertado.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Haga clic en la carpeta **C/C++** .

1. Haga clic en la página de propiedades **Archivos de salida** .

1. Modifique la propiedad **Código fuente con atributos expandidos** .

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.ExpandAttributedSource%2A>.

## <a name="see-also"></a>Vea también

[Archivo de salida (/ F) opciones](../../build/reference/output-file-f-options.md)
[opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)