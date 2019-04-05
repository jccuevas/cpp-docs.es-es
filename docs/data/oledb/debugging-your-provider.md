---
title: Depurar un proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: 21d4cb455413c3f7cbcbed02cdd4c364a469426d
ms.sourcegitcommit: c7f90df497e6261764893f9cc04b5d1f1bf0b64b
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/05/2019
ms.locfileid: "59033885"
---
# <a name="debugging-your-provider"></a>Depurar un proveedor

Hay dos maneras de depurar el proveedor:

- Dado que se crean los proveedores en proceso, puede crear código consumidor mediante las plantillas de consumidor OLE DB y el paso en el proveedor con normalidad.

- Puede usar varias utilidades que vienen con Visual C++.

## <a name="to-use-debugging"></a>Para usar la depuración

1. Abra el proyecto de proveedor.

1. En el **proyectos** menú, haga clic en **propiedades**.

1. En el **páginas de propiedades** cuadro de diálogo, haga clic en el **depuración** ficha.

1. Seleccione opciones según sea necesario, haga clic en **Aceptar**.

1. Establecer puntos de interrupción y, a continuación, depurar como de costumbre.

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)