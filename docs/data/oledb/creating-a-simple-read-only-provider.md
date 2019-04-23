---
title: Crear un proveedor sencillo de sólo lectura
ms.date: 10/26/2018
helpviewer_keywords:
- OLE DB providers, creating
- OLE DB provider templates, creating providers
ms.assetid: ade8ccdd-9ea4-4e46-a964-18460c2a2401
ms.openlocfilehash: a80678f6bc512c45c0df2ea5cbfc4708f1252ac0
ms.sourcegitcommit: 72583d30170d6ef29ea5c6848dc00169f2c909aa
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 04/18/2019
ms.locfileid: "59035366"
---
# <a name="creating-a-simple-read-only-provider"></a>Crear un proveedor sencillo de sólo lectura

Cuando haya creado un proveedor OLE DB mediante el **Asistente para proyectos ATL** y **el Asistente para proveedores OLE DB ATL**, puede agregar otras funcionalidades que desea admitir. Empezar a diseñar su proveedor examinando el tipo de datos que se va a enviar al consumidor y bajo qué condiciones. Es especialmente importante determinar si necesita admitir los comandos, transacciones y otros objetos opcionales. Un buen diseño por adelantado acelerará la implementación y pruebas.

En el ejemplo se presenta en dos partes:

- La primera parte se muestra cómo [crear un proveedor sencillo de sólo lectura](../../data/oledb/implementing-the-simple-read-only-provider.md) que lee un par de cadenas.

- La segunda parte muestra cómo [mejorar un proveedor sencillo de sólo lectura](../../data/oledb/enhancing-the-simple-read-only-provider.md) agregando el `IRowsetLocate` interfaz.

## <a name="see-also"></a>Vea también

[Crear un proveedor OLE DB](../../data/oledb/creating-an-ole-db-provider.md)<br/>
