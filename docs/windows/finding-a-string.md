---
title: Buscar una cadena | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.string
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], searching
- strings [C++]
ms.assetid: c2497173-f356-4f77-97d6-f0ac41782510
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 294154f084bbb2becc4218541887faf32b9600f8
ms.sourcegitcommit: 6f8dd98de57bb80bf4c9852abafef1c35a7600f1
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "42601770"
---
# <a name="finding-a-string"></a>Buscar una cadena

Puede buscar una o varias cadenas en la tabla de cadenas y usar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) con el **buscar en archivos** comando (**editar** menú) para buscar todas las instancias de cadenas que coincide con un patrón.

### <a name="to-find-a-string-in-the-string-table"></a>Para buscar una cadena en la tabla de cadenas

1. Abra la tabla de cadenas haciendo doble clic en el icono correspondiente en [vista de recursos](../windows/resource-view-window.md).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. En el **editar** menú, haga clic en **buscar y reemplazar**, a continuación, elija **encontrar**.

3. En el **buscar** cuadro, seleccione una cadena de búsqueda anterior en la lista desplegable o escriba el título texto o identificador de recurso de la cadena que desea buscar.

4. Seleccione cualquiera de los **buscar** opciones.

5. Haga clic en **Buscar siguiente**.

   > [!TIP]
   > Para usar expresiones regulares al buscar archivos, use el **buscar en archivos** comando. Escriba una expresión regular para coincidir con un patrón o haga clic en el botón a la derecha de la **buscar** cuadro para mostrar una lista de expresiones regulares de búsqueda. Al seleccionar una expresión de esta lista, se usará como el texto de búsqueda en el **buscar** cuadro. Si utiliza expresiones regulares, asegúrese del **usar: expresiones regulares** casilla está activada.

Para obtener información sobre cómo agregar recursos a proyectos administrados (aquellos que tienen como destino common language runtime), consulte [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Tutorial: uso de recursos para la localización con ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cadenas](../windows/string-editor.md)  