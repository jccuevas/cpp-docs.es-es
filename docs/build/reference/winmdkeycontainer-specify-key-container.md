---
title: /WINMDKEYCONTAINER (Especificar contenedor de claves)
ms.date: 11/04/2016
f1_keywords:
- VC.Project.VCLinkerTool.WINMDKEYCONTAINER
ms.assetid: c2fc44dc-7cb5-42b9-897f-1b124928f2f7
ms.openlocfilehash: 0b6cb42fc391d94634ae90e5a4cc17e69a14ff09
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57813076"
---
# <a name="winmdkeycontainer-specify-key-container"></a>/WINMDKEYCONTAINER (Especificar contenedor de claves)

Especifica un contenedor de claves para firmar un archivo de metadatos de Windows (.winmd).

```
/WINMDKEYCONTAINER:name
```

## <a name="remarks"></a>Comentarios

Es similar a la [/keycontainer](keycontainer-specify-a-key-container-to-sign-an-assembly.md) opción del vinculador que se aplica a un archivo (.winmd).

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [propiedades de compilación y el compilador de C++ establece en Visual Studio](../working-with-project-properties.md).

1. Seleccione el **vinculador** carpeta.

1. Seleccione el **Windows metadatos** página de propiedades.

1. En el **contenedor de claves de metadatos de Windows** , escriba la ubicación.

## <a name="see-also"></a>Vea también

[Referencia MSVC del vinculador](linking.md)<br/>
[Opciones del vinculador MSVC](linker-options.md)
