---
title: /WINMDDELAYSIGN (firmar parcialmente un archivo winmd)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDDelaySign
ms.assetid: 445cd602-62cb-400a-8e3a-4beb6572724d
ms.openlocfilehash: 5e6eab3fbc40543b634f03da826d3bd3477b9623
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/23/2019
ms.locfileid: "62316605"
---
# <a name="winmddelaysign-partially-sign-a-winmd"></a>/WINMDDELAYSIGN (firmar parcialmente un archivo winmd)

Habilita la firma parcial de un archivo de metadatos en tiempo de ejecución de Windows (.winmd) colocando la clave pública en el archivo.

```
/WINMDDELAYSIGN[:NO]
```

## <a name="remarks"></a>Comentarios

Es similar a la [/DELAYSIGN](delaysign-partially-sign-an-assembly.md) opción del vinculador que se aplica al archivo de winmd. Use **/WINMDDELAYSIGN** si desea colocar solo la clave pública en el archivo de winmd. De forma predeterminada, el vinculador actúa como si **/winmddelaysign: no** se especificaron; es decir, no inicie el archivo de winmd.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione el **Windows metadatos** página de propiedades.

1. En el **Retrasar firma de metadatos de Windows** lista desplegable, seleccione la opción que desee.

## <a name="see-also"></a>Vea también

[Referencia del enlazador MSVC](linking.md)<br/>
[Opciones del enlazador MSVC](linker-options.md)
