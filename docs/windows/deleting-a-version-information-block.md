---
title: Eliminación de un bloque de información de versión (C++)
ms.date: 11/04/2016
f1_keywords:
- vc.editors.version
helpviewer_keywords:
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
ms.assetid: 4e1641eb-d5b2-4183-b273-bc5b51af1537
ms.openlocfilehash: e0bdc719e3ca3a3ffa4493f1d7c578a91733a7f3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50648310"
---
# <a name="deleting-a-version-information-block-c"></a>Eliminación de un bloque de información de versión (C++)

### <a name="to-delete-a-version-information-block"></a>Para eliminar un bloque de información de versión

1. Para abrir el recurso de información de versión, haga doble clic en su icono en la [Vista de recursos](../windows/resource-view-window.md).

   > [!NOTE]
   > Si el proyecto no contuviera un archivo .rc, vea [Crear un nuevo archivo de script de recursos](../windows/how-to-create-a-resource-script-file.md).

2. Haga clic en el encabezado de bloque que quiera eliminar y después elija **Eliminar bloque de información de versión** en el menú contextual.

   Este comando elimina el encabezado seleccionado y deja intacta la información de versión restante. Tenga en cuenta que no se puede deshacer la acción.

Para obtener información sobre cómo agregar recursos a proyectos administrados, vea [Resources in Desktop Apps](/dotnet/framework/resources/index) en el *Guía del desarrollador de .NET Framework*. Para obtener información sobre cómo agregar manualmente archivos de recursos a proyectos administrados, acceder a los recursos, mostrar recursos estáticos y asignar cadenas de recursos a propiedades, vea [crear archivos de recursos para las aplicaciones de escritorio](/dotnet/framework/resources/creating-resource-files-for-desktop-apps). Para obtener información sobre la globalización y localización de recursos en aplicaciones administradas, vea [Globalizar y localizar aplicaciones de .NET Framework](/dotnet/standard/globalization-localization/index).

## <a name="requirements"></a>Requisitos

Win32

## <a name="see-also"></a>Vea también

[Editor de la información de versión](../windows/version-information-editor.md)<br/>
[Información de versiones (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)