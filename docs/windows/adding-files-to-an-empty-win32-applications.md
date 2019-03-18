---
title: Agregar archivos a una aplicación de Win32 vacía
ms.date: 11/04/2016
helpviewer_keywords:
- empty projects [C++], adding files
- projects [C++], adding items
- blank projects
- files [C++], adding to projects
ms.assetid: 070098e8-0396-49fe-a697-3daa2f1be6de
ms.openlocfilehash: 8facd371ad2dddbb8ce239af5ca536b21a606807
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818211"
---
# <a name="adding-files-to-an-empty-win32-applications"></a>Agregar archivos a una aplicación de Win32 vacía

### <a name="to-add-your-files-to-an-empty-windows-desktop-application"></a>Para agregar sus archivos a una aplicación de escritorio de Windows vacía

1. Seleccione el directorio en el **Explorador de soluciones**.

2. Haga clic con el botón secundario en el nombre del directorio, haga clic en **Agregar** en el menú contextual y luego haga clic en **Elemento existente**.

3. En el **cuadro de diálogo Agregar elemento existente**, desplácese hasta los archivos que quiera agregar al proyecto.

4. Haga clic en **Aceptar**.

Para agregar los archivos que no son ni de origen, encabezado ni archivos de recursos al proyecto, haga clic en el **solución** nodo **el Explorador de soluciones** y agregue los archivos al proyecto de la misma manera. Un **varios** se creará una carpeta que contenga los demás archivos del proyecto.

> [!NOTE]
> Antes de compilar el proyecto, debe especificar opciones de compilación para estos archivos, para que se incluyan correctamente en la aplicación finalizada. Para más información, vea [Especificar la configuración del proyecto con páginas de propiedades](../build/reference/property-pages-visual-cpp.md) y [Creación de un programa C/C++](../build/building-c-cpp-programs.md).

## <a name="see-also"></a>Vea también

[Creación de una aplicación de escritorio de Windows vacía](../windows/creating-an-empty-windows-desktop-application.md)
