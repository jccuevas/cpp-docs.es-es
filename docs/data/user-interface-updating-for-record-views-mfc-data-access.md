---
title: Actualización de la interfaz de usuario para vistas de registros (acceso a datos MFC)
ms.date: 11/04/2016
helpviewer_keywords:
- user interfaces, updating
- menus, updating as context changes
- record views, user interface
ms.assetid: 2c7914b6-2dc3-40c3-b2f2-8371da2a4063
ms.openlocfilehash: 9bfb907d21c928c605b304c595acb834d0046e35
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80209058"
---
# <a name="user-interface-updating-for-record-views--mfc-data-access"></a>Actualización de la interfaz de usuario para vistas de registros (acceso a datos MFC)

`CRecordView` proporciona controladores de actualización predeterminados de la interfaz de usuario para los comandos de navegación. Estos controladores automatizan la habilitación y la deshabilitación de los objetos de la interfaz de usuario, como los elementos de menú y los botones de la barra de herramientas. El Asistente para aplicaciones proporciona menús estándar y, si elige la opción de la **barra de herramientas acoplable** , un conjunto de botones de la barra de herramientas para los comandos. Si crea una clase de vista de registros con `CRecordView`, es posible que le interese agregar a la aplicación objetos de interfaz de usuario similares.

### <a name="to-create-menu-resources-with-the-menu-editor"></a>Cómo crear recursos de menú con el editor de menús

1. Al hacer referencia a la información sobre cómo usar el [Editor de menús](../windows/menu-editor.md), cree su propio menú con los mismos cuatro comandos.

#### <a name="to-create-toolbar-buttons-with-the-graphics-editor"></a>Cómo crear botones de barra de herramientas con el editor de gráficos

1. En la información sobre el uso del [Editor](../windows/toolbar-editor.md)de la barra de herramientas, edite el recurso de la barra de herramientas para agregar botones de barra de herramientas a los comandos de navegación por registros.

## <a name="see-also"></a>Consulte también

[Admitir la navegación en una vista de registros](../data/supporting-navigation-in-a-record-view-mfc-data-access.md)<br/>
[Usar una vista de registros](../data/using-a-record-view-mfc-data-access.md)
