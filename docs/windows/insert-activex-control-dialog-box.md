---
title: Insertar cuadro de diálogo Control de ActiveX | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.insertActiveXControls
dev_langs:
- C++
helpviewer_keywords:
- Insert ActiveX Control dialog box
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 0cf6c5efb0c7613c1332ce05483bd311b037a9b8
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/29/2018
ms.locfileid: "43194487"
---
# <a name="insert-activex-control-dialog-box"></a>Insertar control ActiveX (cuadro de diálogo)

Este cuadro de diálogo permite [insertar controles ActiveX en el cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md) mientras usa la [editor de cuadro de diálogo](../windows/dialog-editor.md).

### <a name="activex-control"></a>Control ActiveX

Muestra una lista de controles Active X. Insertar un control de este cuadro de diálogo no genera una clase contenedora. Si necesita una clase contenedora, utilice [vista de clases](https://msdn.microsoft.com/8d7430a9-3e33-454c-a9e1-a85e3d2db925) para crear uno (para obtener más información, consulte [agregar una clase](../ide/adding-a-class-visual-cpp.md)). Si un control ActiveX no aparece en este cuadro de diálogo, intente instalar el control de acuerdo con las instrucciones del proveedor.

### <a name="path"></a>Ruta de acceso

Muestra el archivo donde se encuentra el control ActiveX.

Puede colocar controles en el **cuadro de herramientas** ventana para facilitar el acceso. Para obtener más información, consulte [cuadro de diálogo Personalizar cuadro de herramientas](https://msdn.microsoft.com/bd07835f-18a8-433e-bccc-7141f65263bb).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cuadros de diálogo (pestaña, cuadro de herramientas)](../windows/dialog-editor-tab-toolbox.md)  
[Archivos de recursos](../windows/resource-files-visual-studio.md)  
[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)