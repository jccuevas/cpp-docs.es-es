---
title: Agregar valores a un Control de cuadro combinado | Documentos de Microsoft
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
- combo boxes [C++], Data property
- controls [Visual Studio], testing values in combo boxes
- combo boxes [C++], adding values
- combo boxes [C++], previewing values
- controls [C++], testing values in combo boxes
- Data property
- combo boxes [C++], testing values
ms.assetid: 22a78f98-fada-48b3-90d8-7fa0d8e4de51
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: c81e40de56970571ad78ceea86084b7ff7b82227
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
---
# <a name="adding-values-to-a-combo-box-control"></a>Agregar valores a un control de cuadro combinado
Puede agregar valores a un control de cuadro combinado siempre y cuando tenga el editor de cuadro de diálogo Abrir.  
  
> [!TIP]
>  Es una buena idea agregar todos los valores al cuadro combinado *antes de* el tamaño del cuadro en el editor de cuadro de diálogo o podría truncarse el texto que debe aparecer en el control combinado.  
  
#### <a name="to-enter-values-into-a-combo-box-control"></a>Para escribir valores en un control de cuadro combinado  
  
1.  Seleccione el control de cuadro combinado haciendo clic en él.  
  
2.  En el [ventana propiedades](/visualstudio/ide/reference/properties-window), desplácese hacia abajo hasta la **datos** propiedad.  
  
    > [!NOTE]
    >  Si se muestran las propiedades agrupadas por tipo, **datos** aparece en la **varios** propiedades.  
  
3.  Haga clic en el área de valores de la **datos** propiedad y el tipo de los valores de datos, separados por punto y coma.  
  
    > [!NOTE]
    >  No incluya espacios entre los valores porque podrían afectar al orden alfabético de la lista desplegable.  
  
4.  Haga clic en **ENTRAR** cuando haya terminado de agregar valores.  
  
 Para obtener información sobre cómo agrandar la parte desplegable de un cuadro combinado, vea [establecer el tamaño del cuadro combinado y su lista de desplegable](setting-the-size-of-the-combo-box-and-its-drop-down-list.md).  
  
> [!NOTE]
>  No se puede agregar valores a proyectos Win32 mediante este procedimiento (la **datos** propiedad aparece en gris para proyectos Win32). Dado que los proyectos de Win32 no tienen las bibliotecas que agregan esta funcionalidad, debe agregar valores a un cuadro combinado con un proyecto Win32 mediante programación.  
  
#### <a name="to-test-the-appearance-of-values-in-a-combo-box"></a>Para probar la apariencia de los valores de un cuadro combinado  
  
1.  Después de escribir valores en la **datos** propiedad, haga clic en el **prueba** situado en la [barra de herramientas del Editor de cuadro de diálogo](../windows/showing-or-hiding-the-dialog-editor-toolbar.md).  
  
     Pruebe a desplazarse hacia abajo en la lista valor completo. Aparecen los valores exactamente como se escriben en el **datos** propiedad en la ventana Propiedades. No hay ninguna comprobación de mayúsculas y minúsculas o esté bien escrito.  
  
     Presione ESC para volver al editor de cuadros de diálogo.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
### <a name="requirements"></a>Requisitos  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Controles de cuadros de diálogo](../windows/controls-in-dialog-boxes.md)   
 [Controles](../mfc/controls-mfc.md)

