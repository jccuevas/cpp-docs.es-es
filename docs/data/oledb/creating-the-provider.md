---
title: Crear un proveedor | Microsoft Docs
ms.custom: ''
ms.date: 10/15/2018
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- OLE DB providers, creating
ms.assetid: 2506ba8f-010d-4231-aac1-387432f7b6b9
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 0dbdf7350eeba1a29392bafc2f099a857e212e37
ms.sourcegitcommit: db6b2ad3195e71abfb60b62f3f015f08b0a719d0
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/18/2018
ms.locfileid: "49410751"
---
# <a name="creating-the-provider"></a>Crear un proveedor

## <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Para crear un proveedor OLE DB con el Asistente para proveedores OLE DB ATL

1. Haga clic en el proyecto.

1. En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar clase**.

1. En el **Agregar clase** cuadro de diálogo **instalado** > **Visual C++** > **ATL**, seleccione el **Proveedor OLEDB ATL** icono y, a continuación, haga clic en **abierto**.

1. En el **el Asistente para proveedores OLE DB ATL**, escriba un nombre corto para el proveedor en el **nombre corto** cuadro. Los temas siguientes utilizan el nombre corto "MyProvider", pero puede usar otro nombre. Rellenan otros cuadros con nombre según el nombre especificado.

1. Editar otros cuadros con nombre, si es necesario. Además de los nombres de objeto y el archivo, puede modificar lo siguiente:

   - **Coclase**: el nombre que utiliza COM para crear el proveedor.

   - **Id. de programa**: el identificador de programación, que es una cadena de texto que se puede usar en lugar de un GUID.

   - **Versión**: se utiliza con los ProgID y Coclass para generar un identificador de programación dependientes de la versión.

1. Haga clic en **Finalizar**.

## <a name="see-also"></a>Vea también

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)
