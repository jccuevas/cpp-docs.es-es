---
title: -SWAPRUN (cargar los resultados del vinculador en el archivo de intercambio) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.SwapRunFromNet
- /swaprun
- VC.Project.VCLinkerTool.SwapRunFromCD
dev_langs:
- C++
helpviewer_keywords:
- -SWAPRUN linker option
- files [C++], LINK
- LINK tool [C++], output
- linker [C++], copying output to swap file
- swap file for linker output
- output files, linker
- /SWAPRUN linker option
- SWAPRUN linker option
ms.assetid: 4a1e7f46-4399-4161-8dfc-d6a71beaf683
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1867eb55f9ebcaba2d29f7b9b4b2f44a68164390
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717501"
---
# <a name="swaprun-load-linker-output-to-swap-file"></a>/SWAPRUN (Cargar resultados del vinculador en el archivo de intercambio)

```
/SWAPRUN:{NET|CD}
```

## <a name="remarks"></a>Comentarios

La opción /SWAPRUN indica al sistema de operativo que copie primero el enlazador de salida a un archivo de intercambio y, a continuación, ejecute la imagen desde allí. Se trata de una característica de Windows NT 4.0 (y versiones posterior).

Si se especifica NET, el sistema operativo primero copiará la imagen binaria desde la red a un archivo de intercambio y cargarlo desde allí. Esta opción es útil para ejecutar aplicaciones a través de la red. Cuando se especifica el CD, el sistema operativo copiará la imagen en un disco extraíble en un archivo de página y, a continuación, cargarlo.

### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Para establecer esta opción del vinculador en el entorno de desarrollo de Visual Studio

1. Abra el cuadro de diálogo **Páginas de propiedades** del proyecto. Para obtener más información, consulte [establecer las propiedades de un proyecto de Visual C++](../../ide/working-with-project-properties.md).

1. Haga clic en el **vinculador** carpeta.

1. Haga clic en el **sistema** página de propiedades.

1. Modifique una de las propiedades siguientes:

   - **Ejecutar intercambio desde CD**

   - **Ejecutar intercambio desde red**

### <a name="to-set-this-linker-option-programmatically"></a>Para establecer esta opción del vinculador mediante programación

1. Vea las propiedades <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromCD%2A> y <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.SwapRunFromNet%2A>.

## <a name="see-also"></a>Vea también

[Establecer las opciones del vinculador](../../build/reference/setting-linker-options.md)<br/>
[Opciones del vinculador](../../build/reference/linker-options.md)