---
title: Probar un proveedor
ms.date: 10/29/2018
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
ms.openlocfilehash: 722757b93d3423b02340c382b16e08a31626bc01
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 08/15/2019
ms.locfileid: "79544541"
---
# <a name="testing-your-provider"></a>Probar un proveedor

Antes de liberar un proveedor, debe realizar las siguientes pruebas, en el orden indicado. Estas pruebas muestran que el proveedor funciona correctamente para la mayoría de los usuarios potenciales.

1. Pruebe el proveedor con una aplicación de [consumidor](../../data/oledb/creating-an-ole-db-consumer.md) escrita con las plantillas de consumidor OLE DB. El consumidor de pruebas debe cubrir todas las áreas funcionales de su proveedor (todo el código que ha agregado o modificado).

1. Pruebe el proveedor con una aplicación de consumidor escrita con ADO. La mayoría de los desarrolladores (especialmente Microsoft C# Visual Basic y los desarrolladores de Microsoft) usan ADO o ADO.net para aplicaciones de consumidor. El consumidor de pruebas debe cubrir todas las áreas funcionales de su proveedor. Para obtener un ejemplo de una aplicación de consumidor de ADO, vea [ejemplos de código ADO en Microsoft Visual Basic](/previous-versions/ms807514(v=msdn.10)).

1. Ejecute las pruebas de conformidad OLE DB (incluidas las pruebas de conformidad de ADO) para mostrar que el proveedor cumple el estándar de nivel 0 para los proveedores de OLE DB. (Para obtener una explicación del nivel 0, busque **pruebas de conformidad de nivel 0 de OLE DB** en [OLE DB guía del programador](/sql/connect/oledb/ole-db/oledb-driver-for-sql-server-programming). Estas pruebas y la documentación asociada se incluyen con C++ visual en el SDK de acceso a datos. Estas pruebas también ayudan a mostrar que el proveedor se ejecuta correctamente cuando se agregan por otros [proveedores de servicios](../../data/oledb/ole-db-resource-pooling-and-services.md) y son especialmente útiles si se modifican o agregan propiedades. Para obtener más información sobre las pruebas de conformidad, vea el archivo Léame del SDK de acceso a datos, que se encuentra en uno de los CD de Visual Studio.

## <a name="see-also"></a>Consulte también

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)