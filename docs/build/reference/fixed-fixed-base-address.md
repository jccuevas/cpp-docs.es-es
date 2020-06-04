---
title: /FIXED (Dirección base fija)
ms.date: 11/04/2016
f1_keywords:
- /fixed
- VC.Project.VCLinkerTool.FixedBaseAddress
helpviewer_keywords:
- preferred base address for loading program
- /FIXED linker option
- -FIXED linker option
- FIXED linker option
ms.assetid: 929bba5e-b7d8-40ed-943e-056aa3710fc5
ms.openlocfilehash: 6cc89df76e48ee258a7c6608aab12573ab11729b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62292489"
---
# <a name="fixed-fixed-base-address"></a>/FIXED (Dirección base fija)

```
/FIXED[:NO]
```

## <a name="remarks"></a>Comentarios

Indica al sistema operativo que solo debe cargar el programa en su dirección base preferida. Si dicha dirección base no está disponible, el sistema operativo no cargará el archivo. Para obtener más información, consulte [/BASE (dirección base)](base-base-address.md).

/FIXED:NO es el valor predeterminado para un archivo DLL, mientras que /FIXED se utiliza para proyectos de cualquier otro tipo.

Si se especifica /FIXED, LINK no generará una sección de cambio de ubicación en el programa. En tiempo de ejecución, si el sistema operativo no logra cargar el programa en la dirección especificada, emitirá un mensaje de error y no lo cargará.

Si se especifica /FIXED:NO, se generará una sección de cambio de ubicación en el programa.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione el **línea de comandos** página de propiedades.

1. Escriba el nombre de opción y la configuración el **opciones adicionales** cuadro.

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

- Vea <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
