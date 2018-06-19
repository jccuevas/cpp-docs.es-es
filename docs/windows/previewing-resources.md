---
title: Vista previa de recursos | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.resvw.resource.previewing
- vs.resvw.resource.previewing
dev_langs:
- C++
helpviewer_keywords:
- resources [Visual Studio], viewing
- resource previews
- code, viewing
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: 32d0082d050ceb391a4346e2a4a38ff71c3cf2a3
ms.sourcegitcommit: d55ac596ba8f908f5d91d228dc070dad31cb8360
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/08/2018
ms.locfileid: "33878676"
---
# <a name="previewing-resources"></a>Vista previa de recursos
Vista previa de los recursos permite ver recursos gráficos sin abrirlos. Obtener una vista previa también es útil para los archivos ejecutables después de que ha compilado porque los identificadores de recursos cambian a números. Puesto que estos identificadores numéricos a menudo no proporcionan suficiente información, obtener una vista previa de los recursos ayuda a identificarlos con rapidez.  
  
 Puede obtener una vista previa del aspecto visual de los siguientes tipos de recursos:  
  
-   Bitmap  
  
-   Cuadro de diálogo  
  
-   Iconos  
  
-   Menú  
  
-   Cursor  
  
-   Barra de herramientas  
  
 La función de vista previa no se aplica a los recursos de acelerador, manifiesto, tabla de cadenas e información de versión.  
  
### <a name="to-preview-resources"></a>Para obtener una vista previa de recursos  
  
1.  En [vista de recursos](../windows/resource-view-window.md) o una ventana de documento, seleccione el recurso en cuestión (por ejemplo, IDD_ABOUTBOX).  
  
     **Nota** Si el proyecto no contiene un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).  
  
2.  En el [ventana propiedades](/visualstudio/ide/reference/properties-window), haga clic en el **páginas de propiedades** botón.  
  
     \- o -  
  
3.  En el **vista** menú, haga clic en **páginas de propiedades**.  
  
     La página de propiedades para el recurso se abrirá una vista previa de ese recurso. Puede, a continuación, utilice el arriba y abajo teclas de dirección para navegar por el control de árbol en la vista de recursos o la ventana de documento. La página de propiedades permanecerá abierta y mostrará todos los recursos que tiene el foco y es capaz de realizar una vista previa.  
  
 Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [recursos en aplicaciones de escritorio](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework.* Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, tener acceso a recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).  
  
 **Requisitos**  
  
 Win32  
  
## <a name="see-also"></a>Vea también  
 [Cómo: abrir un archivo de Script de recursos fuera de un proyecto (independiente)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)   
 [Editores de recursos](../windows/resource-editors.md)

