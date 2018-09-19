---
title: Agregar información de versión para otro idioma (C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-windows
ms.topic: conceptual
f1_keywords:
- vc.editors.version
dev_langs:
- C++
helpviewer_keywords:
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
ms.assetid: 17f6273c-e1cc-441a-a3d8-f564341cbf20
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- uwp
ms.openlocfilehash: bf01f1d4b1c687ed919b94f651ef7ccf4b0bf45d
ms.sourcegitcommit: f0c90000125a9497bf61e41624de189a043703c0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/10/2018
ms.locfileid: "44313460"
---
# <a name="adding-version-information-for-another-language-c"></a>Agregar información de versión para otro idioma (C++)

### <a name="to-add-version-information-for-another-language-new-info-block"></a>Para agregar información de versión para otro idioma (nuevo bloque de información)

1. Para abrir un recurso de información de versión, haga doble clic en él en la [Vista de recursos](../windows/resource-view-window.md).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. Haga clic con el botón secundario dentro de la tabla de información de versión y elija **Nuevo bloque de información de versión** en el menú contextual.

   Este comando agrega un bloque de información adicional al recurso de información de versión actual y abre sus propiedades correspondientes en la [ventana Propiedades](/visualstudio/ide/reference/properties-window).

3. En la ventana **Propiedades** , elija el idioma apropiado y el juego de caracteres para su nuevo bloque.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de la información de versión](../windows/version-information-editor.md)  
[Información de versión (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)