---
title: 'Cómo: crear un archivo de Script de recursos (C++)'
ms.date: 11/04/2016
helpviewer_keywords:
- rc files [C++], creating
- .rc files [C++], creating
- resource script files [C++], creating
ms.assetid: 82be732a-cdcd-4a58-8de7-976d1418f86b
ms.openlocfilehash: eb884ca7520b34771c73e71c7ee9b4d811d5383c
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50491265"
---
# <a name="how-to-create-a-resource-script-file-c"></a>Cómo: crear un archivo de Script de recursos (C++)

> [!NOTE]
> El **Editor de recursos** no está disponible en las ediciones Express.
>
> Este material se aplica a aplicaciones de escritorio de Windows. Los proyectos en lenguajes .NET no utilizan archivos de script de recursos. Para obtener más información, vea [Archivos de recursos](../windows/resource-files-visual-studio.md).

### <a name="to-create-a-new-resource-script-rc-file"></a>Para crear un nuevo archivo de script de recursos (.rc)

1. Coloca el foco en la carpeta del proyecto existente en **el Explorador de soluciones**, por ejemplo, `MyProject`.

   > [!NOTE]
   > No confunda la carpeta del proyecto con la carpeta de soluciones en **el Explorador de soluciones**. Si coloca el foco en el **solución** carpeta, sus elecciones en el **Agregar nuevo elemento** cuadro de diálogo (en el paso 3) serán diferente.

2. En el menú **Proyecto** , haga clic en **Agregar nuevo elemento**.

3. En el cuadro de diálogo **Agregar nuevo elemento** , haga clic en la carpeta **Visual C++** y elija **Archivo de recursos (.rc)** en el panel de la derecha.

4. Asigne un nombre al archivo de script de recursos en el cuadro de texto **Nombre** y después haga clic en **Abrir**.

A partir de ese momento, podrá [crear](../windows/how-to-create-a-resource.md) y agregar recursos al archivo .rc.

> [!NOTE]
> Solo se puede agregar un script de recursos (archivo .rc) a un proyecto existente que esté cargado en el IDE de Visual Studio. No es posible crear archivos .rc independientes (fuera de un proyecto). [Las plantillas de recursos](../windows/how-to-use-resource-templates.md) (archivos .rct) pueden crearse en cualquier momento.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)