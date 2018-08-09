---
title: Abrir un recurso para editarlo en modo binario | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.binary
dev_langs:
- C++
helpviewer_keywords:
- binary data, editing
- resources [Visual Studio], opening for binary editing
ms.assetid: d3cdb0e4-da66-410d-8e49-b29073ff2929
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 26d1b0ae8923835b0ce06c7312fa185693c6586e
ms.sourcegitcommit: 38af5a1bf35249f0a51e3aafc6e4077859c8f0d9
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/09/2018
ms.locfileid: "40014512"
---
# <a name="opening-a-resource-for-binary-editing"></a>Abrir un recurso para editarlo en modo binario
### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Para abrir un recurso de escritorio de Windows para editarlo en modo binario  
  
1.  En la [Vista de recursos](../windows/resource-view-window.md), seleccione el archivo de recursos específico que quiera editar.  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Haga clic con el botón secundario en el recurso y haga clic en **Abrir datos binarios** en el menú contextual.  
  
    > [!NOTE]
    >  Si usas el [vista de recursos](../windows/resource-view-window.md) ventana para abrir un recurso con un formato que Visual Studio no reconozca (como RCDATA o un recurso personalizado), el recurso se abrirá automáticamente en el **binario** editor.  
  
### <a name="to-open-a-managed-resource-for-binary-editing"></a>Para abrir un recurso para editarlo para la edición binaria  
  
1.  En **el Explorador de soluciones**, seleccione el archivo de recursos específico que desea editar.  
  
2.  Haga clic con el botón secundario en el recurso y elija **Abrir con** en el menú contextual.  
  
3.  En el cuadro de diálogo **Abrir con** , seleccione **Editor binario**.  
  
    > [!NOTE]
    >  Se puede usar el [Editor de imágenes](../windows/image-editor-for-icons.md) y el [Editor binario](binary-editor.md) para trabajar con archivos de recursos en proyectos administrados. Todos los recursos administrados que vaya a editar deberán estar vinculados. Los editores de recursos de Visual Studio no admiten la edición de recursos incrustados.  
  
    > [!NOTE]
    >  Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).   
  
 ![Editor binario](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")  
Datos binarios de un cuadro de diálogo que aparece en el editor binario  
  
 Solo determinados valores ASCII se representan en el editor binario (de 0x20 a 0x7E). Los caracteres extendidos se muestran como puntos en la sección de valor ASCII del editor binario (el panel derecho). Los caracteres "imprimibles" son valores ASCII de 32 a 126.  
  
> [!NOTE]
>  Si desea usar el **binario** editor en un recurso ya se está editando en otra ventana del editor, cierre la ventana del editor en primer lugar.  
  
## <a name="requirements"></a>Requisitos  
 Ninguna  
  
## <a name="see-also"></a>Vea también  
 [Binary Editor](binary-editor.md)