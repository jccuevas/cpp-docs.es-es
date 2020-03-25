---
title: Depurar un proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
ms.openlocfilehash: f80ce5dc82dd2baeefe3410a488a5fefda0e9bf0
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 03/24/2020
ms.locfileid: "80211099"
---
# <a name="debugging-your-provider"></a>Depurar un proveedor

Hay dos maneras de depurar el proveedor:

- Dado que los proveedores se crean en proceso, puede crear código de consumidor mediante el OLE DB plantillas de consumidor y entrar en el proveedor con normalidad.

- Puede usar varias utilidades que se ofrecen con Visual C++.

## <a name="to-use-debugging"></a>Para usar la depuración

1. Abra el proyecto de proveedor.

1. En el menú **proyectos** , haga clic en **propiedades**.

1. En el cuadro de diálogo **páginas de propiedades** , haga clic en la pestaña **depuración** .

1. Seleccione opciones según sea necesario y haga clic en **Aceptar**.

1. Establezca puntos de interrupción y, a continuación, depure como de costumbre.

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)
