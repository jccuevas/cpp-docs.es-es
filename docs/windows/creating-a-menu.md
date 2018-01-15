---
title: "Crear un menú | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords: vc.editors.menu
dev_langs: C++
helpviewer_keywords:
- mnemonics, associating menu items
- menus, associating commands with mnemonic keys
- menus, creating
ms.assetid: 66f94448-9b97-4b73-bf97-10d4bf87cc65
caps.latest.revision: "10"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 7d5d600a168c93b663ebe446ddd912d98fee1b19
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="creating-a-menu"></a>Crear un menú
> [!NOTE]
>  La ventana de recursos no está disponible en las ediciones Express.  
  
### <a name="to-create-a-standard-menu"></a>Para crear un menú estándar  
  
1.  En el menú **Ver** , haga clic en **Vista de recursos** y, a continuación, haga clic con el botón secundario en el encabezado **Menú** y elija **Agregar recurso**. Elija **Menú**.  
  
2.  Seleccione el cuadro **Nuevo elemento** (el rectángulo que contiene "Escriba aquí") en la barra de menús.  
  
     ![Cuadro nuevo elemento en el editor de menús](../windows/media/vcmenueditornewitembox.gif "vcMenuEditorNewItemBox")  
Cuadro Nuevo elemento  
  
3.  Escriba un nombre para el nuevo menú, por ejemplo, "Archivo".  
  
     El texto que escriba aparecerá en el **Editor de menús** y en el cuadro **Leyenda** de la [ventana Propiedades](/visualstudio/ide/reference/properties-window). Puede editar las propiedades del nuevo menú en uno u otro componente.  
  
     Tras asignar un nombre al nuevo menú en la barra de menús, el cuadro de nuevo elemento se desplaza hacia la derecha (para permitir agregar otro menú) y se abre otro cuadro de nuevo elemento debajo del primer menú, donde pueden agregarse otros comandos de menú.  
  
     ![Cuadro nuevo elemento expandido](../windows/media/vcmenueditornewitemboxexpanded.gif "vcMenuEditorNewItemBoxExpanded")  
Cuadro Nuevo elemento con el foco desplazado al escribir el nombre del nuevo menú  
  
    > [!NOTE]
    >  Para crear un menú de un solo elemento en la barra de menús, establezca la propiedad Popup en False.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Editor de menús](../windows/menu-editor.md)