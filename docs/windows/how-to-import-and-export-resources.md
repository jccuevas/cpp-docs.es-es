---
title: 'Cómo: importar y exportar recursos (C++)'
ms.date: 11/04/2016
f1_keywords:
- vs.resvw.resource.importing
- vc.resvw.resource.importing
helpviewer_keywords:
- resources [C++], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [C++], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
ms.openlocfilehash: 2e35526b1b2f0455970a06f42ff2d67c171f3804
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50555277"
---
# <a name="how-to-import-and-export-resources"></a>Cómo: Importar y exportar recursos

Puede importar recursos gráficos (mapas de bits, iconos, cursores y barras de herramientas), archivos HTML y recursos personalizados para usarlos en Visual C++. Puede exportar los mismos tipos de archivos desde un proyecto de Visual C++ para separar archivos que se pueden usar fuera del entorno de desarrollo.

> [!NOTE]
> Los tipos de recursos como los aceleradores, los cuadros de diálogo y las tablas de cadenas no se pueden importar o exportar, porque no son tipos de archivos independientes.

### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Para importar un recurso individual al archivo de recursos actual

1. En [vista de recursos](../windows/resource-view-window.md), haga clic en el nodo para el script de recursos (* .rc) a la que desea agregar un recurso de archivo.

2. Haga clic en **importación** en el menú contextual.

3. Busque y seleccione el nombre de archivo del mapa de bits (.bmp), icono (.ico), cursor (.cur), archivo Html (.htm) o cualquier otro archivo que quiera importar.

4. Haga clic en **Aceptar** para agregar el recurso al archivo seleccionado en **recursos** vista.

   > [!NOTE]
   > El proceso de importación es el mismo, independientemente del tipo de recurso seleccionado. El recurso importado se agrega automáticamente al nodo correspondiente a ese tipo de recurso.

### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Para exportar un mapa de bits, un icono o un cursor como un archivo independiente (para usarlo fuera de Visual C++)

1. En **recursos** ver, haga clic en el recurso que desea exportar.

2. Haga clic en **exportar** en el menú contextual.

3. En el **Exportar recurso** diálogo cuadro, acepte el nombre de archivo actual o escriba uno nuevo.

4. Navegue hasta la carpeta donde desea guardar el archivo y haga clic en **exportar**.

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Editores de recursos](../windows/resource-editors.md)