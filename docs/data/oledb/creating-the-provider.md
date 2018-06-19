---
title: Crear un proveedor | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
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
ms.openlocfilehash: b08d2a2f68d174ae7c92d1d6bc0fa2bbb764fdca
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33097190"
---
# <a name="creating-the-provider"></a>Crear un proveedor
#### <a name="to-create-an-ole-db-provider-with-the-atl-ole-db-provider-wizard"></a>Para crear un proveedor OLE DB con el Asistente para proveedores OLE DB ATL  
  
1.  Haga clic en el proyecto.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar clase**.  
  
3.  En el **Agregar clase** cuadro de diálogo, seleccione la **proveedor OLE DB ATL** icono y, a continuación, haga clic en **abiertos**.  
  
4.  En el Asistente para proveedores OLE DB ATL, escriba un nombre corto para el proveedor en el **nombre corto** cuadro. Los temas siguientes utiliza el nombre corto "MyProvider", pero puede usar otro nombre. Los otros cuadros de nombre se rellenan según el nombre especificado.  
  
5.  Edite los otros cuadros de nombre, si es necesario. Además de los nombres de objeto y el archivo, puede modificar lo siguiente:  
  
    -   **Coclase**: el nombre que utiliza COM para crear el proveedor.  
  
    -   **Id. de programa**: el identificador de programación, que es una cadena de texto que se puede usar en lugar de un GUID.  
  
    -   **Versión**: utilizar con los ProgID y coclass para generar un identificador de programación dependientes de la versión.  
  
6.  Haga clic en **Finalizar**.  
  
## <a name="see-also"></a>Vea también  
 [Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)