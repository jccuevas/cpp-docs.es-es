---
title: /ALLOWBIND (Evitar el enlace de archivos DLL)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.PreventDLLBinding
- /allowbind
helpviewer_keywords:
- /ALLOWBIND linker option
- binding DLLs
- preventing DLL binding
- ALLOWBIND linker option
- -ALLOWBIND linker option
- DLLs [C++], preventing binding
ms.assetid: 30e37e24-12e4-407e-988a-39d357403598
ms.openlocfilehash: d963a7145ab2e8c8872dc21c485bdc8f877b0b76
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "69493144"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Evitar el enlace de archivos DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Comentarios

/ALLOWBIND:NO establece en el encabezado de una DLL un bit que le indica a Bind.exe que la imagen no se puede enlazar. Puede que quiera evitar que una DLL se enlace si se firmó digitalmente (el enlace invalida la firma).

Puede editar una DLL existente para la funcionalidad de/ALLOWBIND con la opción [/ALLOWBIND](allowbind.md) de la utilidad EDITBIN.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para más información, vea [Establecimiento del compilador de C++ y de propiedades de compilación en Visual Studio](../working-with-project-properties.md).

1. Expanda **propiedades de configuración**, vinculador y seleccione **línea de comandos**.

1. Escriba `/ALLOWBIND:NO` en **otras opciones**.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)<br/>
[BindImage (función)](/windows/win32/api/imagehlp/nf-imagehlp-bindimage)<br/>
[BindImageEx función)](/windows/win32/api/imagehlp/nf-imagehlp-bindimageex)
