---
title: Depurar un proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: 15e9df58d4b31a8e69999c9ec7c22af158d08b38
ms.sourcegitcommit: 943c792fdabf01c98c31465f23949a829eab9aad
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 11/07/2018
ms.locfileid: "51265092"
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