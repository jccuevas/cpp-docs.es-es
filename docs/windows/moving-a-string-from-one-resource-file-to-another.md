---
title: Mover una cadena de un archivo de recursos a otro (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], moving between files
- resource script files [C++], moving strings
- string editing, moving strings between resources
- String editor [C++], moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 1255eb0fc00d1b134335807a1f20e6761c49ec90
ms.sourcegitcommit: a9dcbcc85b4c28eed280d8e451c494a00d8c4c25
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/25/2018
ms.locfileid: "50064477"
---
# <a name="moving-a-string-from-one-resource-file-to-another-c"></a>Mover una cadena de un archivo de recursos a otro (C++)

### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Para mover una cadena de archivo de script de un recurso a otro

1. Abra las tablas de cadenas en los dos archivos .rc. (Para obtener más información, consulte [ver recursos en un archivo de Script de recursos fuera de un proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. Haga clic en la cadena que desea mover y elija **cortar** en el menú contextual.

3. Coloque el cursor en el destino **Editor de cadenas** ventana.

4. En el archivo .rc en la que desea mover la cadena, haga clic en y elija **pegar** en el menú contextual.

   > [!NOTE]
   > Si el **ID** o **valor** de conflictos con una cadena desplazada **ID** o **valor** en el archivo de destino, ya sea el **ID** o **valor** de los cambios de la cadena desplazada. Si existe una cadena con el mismo **ID**, el **ID** de los cambios de la cadena desplazada. Si existe una cadena con el mismo **valor**, **valor** de los cambios de la cadena desplazada.

Para obtener información sobre cómo agregar recursos a proyectos administrados (aquellos que tienen como destino common language runtime), consulte [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](/previous-versions/visualstudio/visual-studio-2010/y99d1cd3).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de cadenas](../windows/string-editor.md)<br/>
[Archivos de recursos](../windows/resource-files-visual-studio.md)<br/>
[Personalizar los diseños de ventana](/visualstudio/ide/customizing-window-layouts-in-visual-studio)