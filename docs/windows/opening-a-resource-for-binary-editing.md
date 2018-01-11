---
title: Abrir un recurso para editarlo en modo binario | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.binary
dev_langs: C++
helpviewer_keywords:
- binary data, editing
- resources [Visual Studio], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
caps.latest.revision: "13"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 92a0c0459626f139b7a8d7ae2313439c66d2a11c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="opening-a-resource-for-binary-editing"></a>Abrir un recurso para editarlo en modo binario
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Para abrir un recurso de escritorio de Windows para editarlo en modo binario  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), seleccione el archivo de recursos específico que quiera editar.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Haga clic con el botón secundario en el recurso y haga clic en **Abrir datos binarios** en el menú contextual.  
  
    > [!NOTE]
    >  Si usa la ventana [Vista de recursos](../windows/resource-view-window.md) para abrir un recurso con un formato que Visual Studio no reconozca (como RCDATA o un recurso personalizado), el recurso se abrirá automáticamente en el editor binario.  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>Para abrir un recurso para editarlo para la edición binaria  
  
1.  En el Explorador de soluciones, seleccione el archivo de recursos específico que quiera editar.  
  
2.  Haga clic con el botón secundario en el recurso y elija **Abrir con** en el menú contextual.  
  
3.  En el cuadro de diálogo **Abrir con** , seleccione **Editor binario**.  
  
    > [!NOTE]
    >  Se puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
    > [!NOTE]
    >  Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).   
  
 ![Editor binario](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
Datos binarios de un cuadro de diálogo que aparece en el editor binario  
  
 Solo determinados valores ASCII se representan en el editor binario (de 0x20 a 0x7E). Los caracteres extendidos se muestran como puntos en la sección de valor ASCII del editor binario (el panel derecho). Los caracteres "imprimibles" son valores ASCII de 32 a 126.  
  
> [!NOTE]
>  Si quiere usar el editor binario en un recurso que ya se está editando en otra ventana del editor, cierre primero la otra ventana del editor.  
  
 **Requisitos**  
  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Binary Editor](binary-editor.md)

