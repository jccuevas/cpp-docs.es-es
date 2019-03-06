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
ms.openlocfilehash: 6b6582049dfaac47f1989a5bdf79bfac418ae4e5
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416480"
---
# <a name="allowbind-prevent-dll-binding"></a>/ALLOWBIND (Evitar el enlace de archivos DLL)

```
/ALLOWBIND[:NO]
```

## <a name="remarks"></a>Comentarios

/ALLOWBIND:NO establece en el encabezado de una DLL un bit que le indica a Bind.exe que la imagen no se puede enlazar. Puede que quiera evitar que una DLL se enlace si se firmó digitalmente (el enlace invalida la firma).

Puede editar una DLL existente con la funcionalidad /ALLOWBIND el [/ALLOWBIND](../../build/reference/allowbind.md) opción de la utilidad EDITBIN.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, vea [Trabajar con propiedades del proyecto](../../ide/working-with-project-properties.md).

1. Expanda **propiedades de configuración**, **vinculador**y seleccione **línea de comandos**.

1. Escriba `/ALLOWBIND:NO` en **opciones adicionales**.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)<br/>
[Función BindImage](/windows/desktop/api/imagehlp/nf-imagehlp-bindimage)<br/>
[Función BindImageEx](/windows/desktop/api/imagehlp/nf-imagehlp-bindimageex)
