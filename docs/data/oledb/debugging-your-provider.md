---
title: Depurar un proveedor
ms.date: 11/04/2016
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: e79719075bcd98733031abd63708bea861388cff
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/31/2018
ms.locfileid: "50466231"
---
# <a name="debugging-your-provider"></a>Depurar un proveedor

Hay dos maneras de depurar el proveedor:

- Dado que se crean los proveedores en proceso, puede crear código consumidor mediante las plantillas de consumidor OLE DB y el paso en el proveedor con normalidad.

- Puede usar la utilidad ITEST que se incluye con Visual C++.

## <a name="to-use-the-itest-utility"></a>Para usar la utilidad ITEST

1. Abra el proyecto de proveedor.

1. En el **proyectos** menú, haga clic en **configuración**.

1. En el **páginas de propiedades** cuadro de diálogo, haga clic en el **depurar** ficha.

1. En el **archivo ejecutable para sesión de depuración** , seleccione la aplicación ITEST.

1. Establecer puntos de interrupción y, a continuación, depurar como de costumbre.

## <a name="see-also"></a>Vea también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)