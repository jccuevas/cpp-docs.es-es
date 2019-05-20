---
title: Crear un proveedor sencillo de sólo lectura
ms.date: 05/09/2019
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: 466530cb8c2ebca7f1c87370389309d3a0486e26
ms.sourcegitcommit: fc1de63a39f7fcbfe2234e3f372b5e1c6a286087
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 05/15/2019
ms.locfileid: "65707621"
---
# <a name="creating-a-simple-read-only-provider"></a>Crear un proveedor sencillo de sólo lectura

::: moniker range="vs-2019"

El Asistente para proveedores OLE DB ATL no está disponible en Visual Studio 2019 ni en versiones posteriores.

::: moniker-end

::: moniker range="<=vs-2017"

Cuando haya creado un proveedor OLE DB mediante el **Asistente para proyectos ATL** y el **Asistente para proveedores OLE DB ATL**, puede agregar otras funcionalidades que desea admitir. Empiece a diseñar su proveedor examinando el tipo de datos que se va a enviar al consumidor y bajo qué condiciones. Es especialmente importante determinar si necesita admitir los comandos, las transacciones y otros objetos opcionales. Un buen diseño por adelantado acelerará la implementación y las pruebas.

El ejemplo se presenta en dos partes:

- La primera parte muestra cómo [crear un proveedor sencillo de solo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md) que lee un par de cadenas.

- La segunda parte muestra cómo [mejorar un proveedor sencillo de solo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md) agregando la interfaz `IRowsetLocate`.

::: moniker-end

## <a name="see-also"></a>Vea también

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
