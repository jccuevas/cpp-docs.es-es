---
title: Vista previa de recursos (C++) | Microsoft Docs
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
- resources [C++], viewing
ms.assetid: d6abda66-0e2b-4ac3-a59a-a57b8c6fb70b
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bd5e273a07ed09f54b84d064011874533b55fb88
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/19/2018
ms.locfileid: "46445833"
---
# <a name="previewing-resources"></a>Vista previa de recursos

Vista previa de los recursos permite ver recursos gráficos sin abrirlos. Obtener una vista previa también es útil para los archivos ejecutables después de que haya compilado ya que cambian los identificadores de recursos a los números. Dado que estos identificadores numéricos a menudo no proporcionan suficiente información, vista previa de los recursos ayuda a identificarlos con rapidez.

Puede obtener una vista previa del diseño visual de los siguientes tipos de recursos:

- Bitmap

- Cuadro de diálogo

- Iconos

- Menú

- Cursor

- Barra de herramientas

La función de vista previa no se aplica a los recursos del acelerador, manifiesto, tabla de cadenas e información de versión.

### <a name="to-preview-resources"></a>Para obtener una vista previa de recursos

1. En [vista de recursos](../windows/resource-view-window.md) o una ventana de documento, seleccione el recurso, por ejemplo, **IDD_ABOUTBOX**.

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. En el [ventana propiedades](/visualstudio/ide/reference/properties-window), haga clic en el **páginas de propiedades** botón.

   \- o -

3. En el **vista** menú, haga clic en **páginas de propiedades**.

   El **página de propiedades** para el recurso se abrirá una vista previa de ese recurso. A continuación, puede usar el **seguridad** y **hacia abajo** teclas de flecha para navegar por el árbol de control en **vista de recursos** o la ventana de documento. El **página de propiedades** permanecerá abierta y mostrará todos los recursos que tiene el foco y es capaz de realizar una vista previa.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Procedimiento para abrir un archivo de script de recursos fuera de un proyecto (independiente)](../windows/how-to-open-a-resource-script-file-outside-of-a-project-standalone.md)<br/>
[Editores de recursos](../windows/resource-editors.md)