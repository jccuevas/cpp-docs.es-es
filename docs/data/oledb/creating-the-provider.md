---
title: Crear un proveedor
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
ms.openlocfilehash: 7a8b4caf85ff7d0310c97cb953739796cca21c43
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707578"
---
# <a name="creating-the-provider"></a>Crear un proveedor

::: moniker range="vs-2019"

El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Crear un proveedor OLE DB con el Asistente para proveedores OLE DB ATL

1. Haga clic con el botón derecho en el proyecto.

1. En el menú contextual, haga clic en **Agregar** y después en **Agregar clase**.

1. En el cuadro de diálogo **Agregar clase**, en **Instalado** > **Visual C++** > **ATL**, seleccione el icono de **Proveedor OLEDB ATL** y, a continuación, haga clic en **Abrir**.

1. En el **Asistente para proveedores OLE DB ATL**, escriba un nombre corto para el proveedor en el cuadro **Nombre corto**. En los temas siguientes se usa el nombre corto *Personalizado*, pero puede usar otro. El resto de los cuadros se rellenan según el nombre especificado.

1. Edite los otros cuadros de nombre si lo desea. Además de los nombres de objeto y archivo, puede modificar lo siguiente:

   - **Coclass**: El nombre que utiliza COM para crear el proveedor.

   - **ProgID**: El identificador de programación, que es una cadena de texto que se puede usar en lugar de un GUID.

   - **Version**: Se utiliza con ProgID y Coclass para generar un identificador de programación dependiente de la versión.

1. Haga clic en **Finalizar**.

::: moniker-end

## <a name="see-also"></a>Vea también

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
