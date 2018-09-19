---
title: Convertir una imagen de un formato a otro (Editor de imágenes para iconos) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- images [C++], stand-alone editing
- Image editor [C++], converting image formats
- graphics [C++], converting formats
- images [C++], converting formats
ms.assetid: 0409c2bd-3bd8-4d72-9c71-c683b6cf51be
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 6ef3a2ce99309781ecbfd0c406fe8e0f6f7e0613
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42592123"
---
# <a name="converting-an-image-from-one-format-to-another-image-editor-for-icons"></a>Convertir una imagen de un formato en otro (Editor de imágenes para iconos)

Puede abrir imágenes GIF o JPEG en la **imagen** editor y guardarlos como mapas de bits. Además, puede abrir un archivo de mapa de bits y guardarla como JPEG o GIF. Trabajar con las imágenes no necesitan ser parte de un proyecto para editarlo en el entorno de desarrollo (vea [edición de imágenes independientes](../windows/editing-an-image-outside-of-a-project-image-editor-for-icons.md)).

### <a name="to-convert-an-image-from-one-format-to-another"></a>Para convertir una imagen de un formato a otro

1. Abra la imagen en el **imagen** editor.

2. Desde el **archivo** menú, elija **guardar *filename* como**.

3. En el **Guardar archivo como** cuadro de diálogo el **nombre de archivo** , escriba el nombre de archivo y la extensión que denota el formato que desee.

4. Haga clic en **Guardar**.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Ninguna

## <a name="see-also"></a>Vea también

[Editar recursos gráficos](../windows/editing-graphical-resources-image-editor-for-icons.md)  
[Editor de imágenes para iconos](../windows/image-editor-for-icons.md)