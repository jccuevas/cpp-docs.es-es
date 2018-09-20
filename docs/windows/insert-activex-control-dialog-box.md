---
title: Insertar cuadro de diálogo de Control ActiveX (C++) | Microsoft Docs
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
- Insert ActiveX Control dialog box [C++]
- ActiveX controls [C++], adding to dialog boxes
ms.assetid: 06638ea3-0726-40da-a989-9b89292d0e3d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 9a157649f374dfd1fabbecd6ce60523f4208733b
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46396732"
---
# <a name="insert-activex-control-dialog-box-c"></a>Insertar cuadro de diálogo de Control ActiveX (C++)

Este cuadro de diálogo permite [insertar controles ActiveX en el cuadro de diálogo](../windows/viewing-and-adding-activex-controls-to-a-dialog-box.md) mientras usa la [editor de cuadro de diálogo](../windows/dialog-editor.md).

### <a name="activex-control"></a>Control ActiveX

Muestra una lista de controles Active X. Insertar un control de este cuadro de diálogo no genera una clase contenedora. Si necesita una clase contenedora, utilice [vista de clases](/visualstudio/ide/viewing-the-structure-of-code) para crear uno (para obtener más información, consulte [agregar una clase](../ide/adding-a-class-visual-cpp.md)). Si un control ActiveX no aparece en este cuadro de diálogo, intente instalar el control de acuerdo con las instrucciones del proveedor.

### <a name="path"></a>Ruta de acceso

Muestra el archivo donde se encuentra el control ActiveX.

Puede colocar controles en el **cuadro de herramientas** ventana para facilitar el acceso. Para obtener más información, vea [Cuadro de herramientas](/visualstudio/ide/reference/).

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cuadros de diálogo (pestaña, cuadro de herramientas)](../windows/dialog-editor-tab-toolbox.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)