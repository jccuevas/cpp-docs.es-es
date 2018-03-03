---
title: Mover una cadena de un archivo de recursos a otro | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- strings [C++], moving between files
- resource script files, moving strings
- string editing, moving strings between resources
- String editor, moving strings between files
ms.assetid: 94f8ee81-9b4c-4788-ba95-68c58db38029
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: ecb999052aa23d173a6a4113007cbd8452510e5f
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="moving-a-string-from-one-resource-file-to-another"></a>Mover una cadena de un archivo de recursos a otro
### <a name="to-move-a-string-from-one-resource-script-file-to-another"></a>Para mover una cadena de archivo de script de un recurso a otro  
  
1.  Abra las tablas de cadenas en los archivos .rc. (Para obtener más información, consulte [ver recursos en un archivo de Script de recursos fuera de un proyecto](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md).)  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  Haga clic en la cadena que desea mover y elija **cortar** en el menú contextual.  
  
3.  Coloque el cursor en el destino **Editor de cadenas** ventana.  
  
4.  En el archivo .rc en la que desea mover la cadena, haga clic en y elija **pegar** en el menú contextual.  
  
    > [!NOTE]
    >  Si el **identificador** o **valor** de los conflictos de cadena ha movido a otra **identificador** o **valor** en el archivo de destino, ya sea el **Identificador** o **valor** de los cambios de la cadena desplazada. Si existe una cadena con el mismo **identificador**, el **identificador** de los cambios de la cadena desplazada. Si existe una cadena con el mismo **valor**, **valor** de los cambios de la cadena desplazada.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados (aquellos que tienen como destino common language runtime), vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* . Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de cadenas](../windows/string-editor.md)   
 [Archivos de recursos](../windows/resource-files-visual-studio.md)   
 [Personalizar los diseños de ventana](/visualstudio/ide/customizing-window-layouts-in-visual-studio)   

