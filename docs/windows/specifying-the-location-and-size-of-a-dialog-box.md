---
title: Especificar la ubicación y tamaño de un cuadro de diálogo (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- dialog boxes [C++], size
- dialog boxes [C++], positioning
ms.assetid: 2b7c495e-6595-4cfb-9664-80b2826d0851
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 854e4df84bfc5f75eda8f98fa117c199ba054b3a
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44316580"
---
# <a name="specifying-the-location-and-size-of-a-dialog-box-c"></a>Especificar la ubicación y tamaño de un cuadro de diálogo (C++)

La ubicación y el tamaño de un cuadro de diálogo de C++, así como la ubicación y tamaño de los controles dentro de ella, se miden en unidades de cuadro de diálogo. Los valores de los controles individuales y el cuadro de diálogo aparecen en la esquina inferior derecha de la barra cuando seleccionarlas de estado de Visual Studio.

Hay tres propiedades que se pueden establecer en el [ventana propiedades](/visualstudio/ide/reference/properties-window) para especificar dónde aparecerá un cuadro de diálogo en la pantalla. El **Center** propiedad es un valor booleano; si establece el valor en **True**, el cuadro de diálogo siempre aparecerá en el centro de la pantalla. Si se establece en **False**, a continuación, puede establecer el **XPos** y **YPos** las propiedades para definir explícitamente donde aparecerá el cuadro de diálogo en la pantalla. Las propiedades de posición son valores de desplazamiento de la esquina superior izquierda del área de visualización, que se define como `{X=0, Y=0}`. La posición también se basa en el **Absolute Align** propiedad: si **True**, las coordenadas son relativas a la pantalla; si **False**, las coordenadas son en relación con el cuadro de diálogo ventana del propietario.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)  
[Controles](../mfc/controls-mfc.md)