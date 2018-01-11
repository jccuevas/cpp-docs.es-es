---
title: "Cómo: importar y exportar recursos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- vs.resvw.resource.importing
- vc.resvw.resource.importing
dev_langs: C++
helpviewer_keywords:
- resources [Visual Studio], exporting
- graphics [C++], exporting
- graphics [C++], importing
- resources [Visual Studio], importing
- bitmaps [C++], importing and exporting
- toolbars [C++], importing
- images [C++], importing
- toolbars [C++], exporting
- cursors [C++], importing and exporting
- images [C++], exporting
ms.assetid: 3c9329dc-dcb8-4edd-a600-78e3e572bd89
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: a01269928d0e5b52cca6e2301ad681db61289f80
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-import-and-export-resources"></a>Cómo: Importar y exportar recursos
Puede importar recursos gráficos (mapas de bits, iconos, cursores y barras de herramientas), archivos HTML y recursos personalizados para usarlos en Visual C++. Puede exportar los mismos tipos de archivos desde un proyecto de Visual C++ para separar archivos que se pueden usar fuera del entorno de desarrollo.  
  
> [!NOTE]
>  Los tipos de recursos como los aceleradores, los cuadros de diálogo y las tablas de cadenas no se pueden importar o exportar, porque no son tipos de archivos independientes.  
  
### <a name="to-import-an-individual-resource-into-your-current-resource-file"></a>Para importar un recurso individual al archivo de recursos actual  
  
1.  En [vista de recursos](../windows/resource-view-window.md), haga clic en el nodo para el script de recursos (* .rc) a la que desea agregar un recurso de archivo.  
  
2.  Haga clic en **importación** en el menú contextual.  
  
3.  Busque y seleccione el nombre de archivo del mapa de bits (.bmp), icono (.ico), cursor (.cur), archivo Html (.htm) o cualquier otro archivo que quiera importar.  
  
4.  Haga clic en **Aceptar** para agregar el recurso al archivo seleccionado en **recursos** vista.  
  
    > [!NOTE]
    >  El proceso de importación es el mismo, independientemente del tipo de recurso seleccionado. El recurso importado se agrega automáticamente al nodo correspondiente a ese tipo de recurso.  
  
### <a name="to-export-a-bitmap-icon-or-cursor-as-a-separate-file-for-use-outside-of-visual-c"></a>Para exportar un mapa de bits, un icono o un cursor como un archivo independiente (para usarlo fuera de Visual C++)  
  
1.  En **recursos** ver, haga clic en el recurso que se va a exportar.  
  
2.  Haga clic en **exportar** en el menú contextual.  
  
3.  En el **Exportar recurso** diálogo cuadro, acepte el nombre de archivo actual o escriba uno nuevo.  
  
4.  Navegue hasta la carpeta donde desea guardar el archivo y haga clic en **exportar**.  
  

  
 Requisitos  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Editores de recursos](../windows/resource-editors.md)