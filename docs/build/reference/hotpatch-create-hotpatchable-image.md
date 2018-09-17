---
title: -hotpatch (crear una imagen) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /hotpatch
- VC.Project.VCCLCompilerTool.CreateHotpatchableImage
dev_langs:
- C++
helpviewer_keywords:
- hot patching
- -hotpatch compiler option [C++]
- /hotpatch compiler option [C++]
- hotpatching
ms.assetid: aad539b6-c053-4c78-8682-853d98327798
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 97e1b6197ea60099457db7788ad7e24b96c9fcb8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45716981"
---
# <a name="hotpatch-create-hotpatchable-image"></a>/hotpatch (Crear una imagen a la que se puede aplicar una revisión reciente)

Prepara una imagen para aplicar una revisión activa.

## <a name="syntax"></a>Sintaxis

```
/hotpatch
```

## <a name="remarks"></a>Comentarios

Cuando **/hotpatch** se utiliza en una compilación, el compilador garantiza que primera instrucción de cada función sea al menos dos bytes, que es necesario para aplicar una revisión reciente.

Para completar la preparación para que hotpatch de imagen, después de usar **/hotpatch** para compilar, debe usar [/FUNCTIONPADMIN (crear una imagen)](../../build/reference/functionpadmin-create-hotpatchable-image.md) para vincular. Cuando se compila y vincula una imagen mediante el uso de una invocación de cl.exe, **/hotpatch** implica **/functionpadmin**.

Dado que las instrucciones siempre son dos bytes o mayores en la arquitectura ARM y porque x64 compilación siempre se trata como si **/hotpatch** se ha especificado, no tiene que especificar **/hotpatch** cuando compilar para estos destinos; Sin embargo, todavía debe vincular mediante **/functionpadmin** para crear imágenes a las para ellos. El **/hotpatch** solo afecta a x86 compilación de opción de compilador.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del compilador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Seleccione el **C o C++** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Agregue la opción del compilador para la **opciones adicionales** cuadro.

### <a name="to-set-this-compiler-option-programmatically"></a>Para establecer esta opción del compilador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="guidance"></a>Orientación

Para obtener más información acerca de la administración de actualizaciones, vea "Security Guidance for Update Management" en [ http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx ](http://www.microsoft.com/technet/security/guidance/PatchManagement.mspx).

## <a name="see-also"></a>Vea también

[Opciones del compilador](../../build/reference/compiler-options.md)<br/>
[Establecer las opciones del compilador](../../build/reference/setting-compiler-options.md)