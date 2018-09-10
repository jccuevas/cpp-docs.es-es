---
title: Agregar archivos a una aplicación de Win32 vacía | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- empty projects [C++], adding files
- projects [C++], adding items
- blank projects
- files [C++], adding to projects
ms.assetid: 070098e8-0396-49fe-a697-3daa2f1be6de
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 2801ddf7169bfd8d9ede93ada28cd4716057661c
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44315748"
---
# <a name="adding-files-to-an-empty-win32-applications"></a>Agregar archivos a una aplicación de Win32 vacía

### <a name="to-add-your-files-to-an-empty-windows-desktop-application"></a>Para agregar sus archivos a una aplicación de escritorio de Windows vacía

1. Seleccione el directorio en el **Explorador de soluciones**.

2. Haga clic con el botón secundario en el nombre del directorio, haga clic en **Agregar** en el menú contextual y luego haga clic en **Elemento existente**.

3. En el **cuadro de diálogo Agregar elemento existente**, desplácese hasta los archivos que quiera agregar al proyecto.

4. Haga clic en **Aceptar**.

Para agregar los archivos que no son ni de origen, encabezado ni archivos de recursos al proyecto, haga clic en el **solución** nodo **el Explorador de soluciones** y agregue los archivos al proyecto de la misma manera. Un **varios** se creará una carpeta que contenga los demás archivos del proyecto.

> [!NOTE]
> Antes de compilar el proyecto, debe especificar opciones de compilación para estos archivos, para que se incluyan correctamente en la aplicación finalizada. Para más información, vea [Especificar la configuración del proyecto con páginas de propiedades](../ide/property-pages-visual-cpp.md) y [Creación de un programa C/C++](../build/building-c-cpp-programs.md).

## <a name="see-also"></a>Vea también

[Creación de una aplicación de escritorio de Windows vacía](../windows/creating-an-empty-windows-desktop-application.md)  
