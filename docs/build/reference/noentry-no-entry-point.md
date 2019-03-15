---
title: /NOENTRY (Sin punto de entrada)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.ResourceOnlyDLL
- /noentry
helpviewer_keywords:
- entry points [C++], linker specifying
- -NOENTRY linker option
- resource-only DLLs [C++], creating
- NOENTRY linker option
- /NOENTRY linker option [C++]
- DLLs [C++], creating
ms.assetid: 0214dd41-35ad-43ab-b892-e636e038621a
ms.openlocfilehash: c750fd94e21eec39a25acf216a452faaa277bf7c
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57811457"
---
# <a name="noentry-no-entry-point"></a>/NOENTRY (Sin punto de entrada)

```
/NOENTRY
```

## <a name="remarks"></a>Comentarios

La opción /NOENTRY es necesaria para la creación de un archivo DLL solo de recursos que contenga código no ejecutable. Para obtener más información, consulte [crear un archivo DLL de Resource-Only](../creating-a-resource-only-dll.md).

Se utiliza para evitar que LINK vincule una referencia con `_main` en la DLL.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione el **avanzadas** página de propiedades.

1. Modificar el **ningún punto de entrada** propiedad.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.ResourceOnlyDLL%2A>.

## <a name="see-also"></a>Vea también

[Creación de un archivo DLL de recursos](../creating-a-resource-only-dll.md)<br/>
[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
