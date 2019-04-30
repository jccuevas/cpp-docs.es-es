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
ms.openlocfilehash: bd9976e434441d2480386ee6fa3d0315fd8d2ef5
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62295156"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Evitar el enlace de archivos DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Comentarios

/ALLOWBIND:NO establece en el encabezado de una DLL un bit que le indica a Bind.exe que la imagen no se puede enlazar. Puede que quiera evitar que una DLL se enlace si se firmó digitalmente (el enlace invalida la firma).

Puede editar una DLL existente con la funcionalidad /ALLOWBIND el [/ALLOWBIND](allowbind.md) opción de la utilidad EDITBIN.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Expanda **propiedades de configuración**, **vinculador**y seleccione **línea de comandos**.

1. Escriba `/ALLOWBIND:NO` en **opciones adicionales**.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)<br/>
[Función BindImage](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)<br/>
[Función BindImageEx](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)
