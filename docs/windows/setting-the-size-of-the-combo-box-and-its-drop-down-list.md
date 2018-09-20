---
title: Establecer el tamaño de cuadro combinado y de su lista desplegable | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.dialog.combo
dev_langs:
- C++
helpviewer_keywords:
- combo boxes, sizing
- controls [C++], sizing
ms.assetid: 51fb53cf-9ddf-4a20-962e-8553938e55ee
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 8bd2a81c10855dfe1d409b34612956616018dab7
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46413463"
---
# <a name="setting-the-size-of-the-combo-box-and-its-drop-down-list"></a>Establecer el tamaño de un cuadro combinado y de su lista desplegable

Puede ajustar el tamaño de un cuadro combinado cuando se agrega al cuadro de diálogo. También puede especificar el tamaño del cuadro de lista desplegable.

### <a name="to-size-a-combo-box"></a>Para cambiar el tamaño de un cuadro combinado

1. Seleccione el control de cuadro combinado en el cuadro de diálogo.

   Inicialmente, solo los controladores de tamaño de la derecha e izquierda están activos.

2. Use los controladores de tamaño para establecer el ancho del cuadro combinado.

También puede establecer el tamaño vertical de la parte desplegable del cuadro combinado.

#### <a name="to-set-the-size-of-the-combo-box-drop-down-list"></a>Para establecer el tamaño combinado de la lista desplegable del cuadro

1. Haga clic en el botón de flecha de lista desplegable situado a la derecha del cuadro combinado.

   ![Flecha de un cuadro combinado en un proyecto MFC](../mfc/media/vccomboboxarrow.gif "vcComboBoxArrow")

   El contorno del control cambia para mostrar el tamaño del cuadro combinado con el área de la lista desplegable extendido.

2. Use el controlador de tamaño inferior para cambiar el tamaño inicial del área de la lista desplegable.

   ![Cuadro combinado&#45;ajuste de tamaño de cuadro en un proyecto MFC](../mfc/media/vccomboboxsizing.gif "vcComboBoxSizing")

3. Haga clic en la flecha desplegable para cerrar la parte de la lista desplegable del cuadro combinado.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Adición de valores a un control de cuadro combinado](../windows/adding-values-to-a-combo-box-control.md)<br/>
[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)<br/>
[Controles](../mfc/controls-mfc.md)