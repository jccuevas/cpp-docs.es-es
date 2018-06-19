---
title: Buscar una cadena | Documentos de Microsoft
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
ms.openlocfilehash: 3763baf0f085dc72040ab22c9efd38e8aa8068f7
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33875739"
---
# <a name="finding-a-string"></a>Buscar una cadena
Puede buscar una o varias cadenas en la tabla de cadenas y usar [expresiones regulares](/visualstudio/ide/using-regular-expressions-in-visual-studio) con el **buscar en archivos** comando (**editar** menú) para buscar todas las instancias de cadenas que coinciden con un patrón.  
  
### <a name="to-find-a-string-in-the-string-table"></a>Para buscar una cadena en la tabla de cadenas  
  
1.  Abra la tabla de cadenas haciendo doble clic en su icono en [vista de recursos](../windows/resource-view-window.md).  
  
    > [!NOTE]
    >  Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el **editar** menú, haga clic en **buscar y reemplazar**, a continuación, elija **buscar**.  
  
3.  En el **buscar** cuadro, seleccione una cadena de búsqueda anterior en la lista desplegable o escriba el identificador de recurso o texto de título de la cadena que desea buscar.  
  
4.  Seleccione cualquiera de los **buscar** opciones.  
  
5.  Haga clic en **Buscar siguiente**.  
  
    > [!TIP]
    >  Para usar expresiones regulares para buscar archivos, use la **buscar en archivos** comando. Escriba una expresión regular para coincidir con un patrón o haga clic en el botón a la derecha de la **buscar** cuadro para mostrar una lista de expresiones regulares de búsqueda. Cuando se selecciona una expresión de esta lista, se usará como el texto de búsqueda en el **buscar** cuadro. Si utiliza expresiones regulares, asegúrese del **usar: expresiones regulares** casilla está activada.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados (aquellos que tienen como destino common language runtime), vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* . Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, obtener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [Tutorial: adaptar Windows Forms](http://msdn.microsoft.com/en-us/9a96220d-a19b-4de0-9f48-01e5d82679e5) y [Walkthrough: Using Resources for Localization with ASP.NET](http://msdn.microsoft.com/Library/bb4e5b44-e2b0-48ab-bbe9-609fb33900b6).  
  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de cadenas](../windows/string-editor.md)   

