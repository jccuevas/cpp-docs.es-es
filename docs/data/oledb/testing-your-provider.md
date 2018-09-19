---
title: Probar un proveedor | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- testing, OLE DB providers
- testing providers
- OLE DB providers, testing
ms.assetid: bf824fe4-81af-4ffb-beb3-4fa2928dc450
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: d175216fedb2e6a9139d970fc7696672576f7423
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 09/18/2018
ms.locfileid: "46042902"
---
# <a name="testing-your-provider"></a>Probar un proveedor

Antes de liberar un proveedor, debe realizar las pruebas siguientes, en el orden indicado. Estas pruebas aseguran de que el proveedor funciona correctamente para la mayoría de los usuarios potencial.  
  
1. Pruebe el proveedor mediante un [consumidor](../../data/oledb/creating-an-ole-db-consumer.md) aplicación escrita con las plantillas de consumidor OLE DB. El consumidor de prueba debe cubrir todas las áreas funcionales del proveedor (todo el código que ha agregado o modificado).  
  
1. Probar el proveedor mediante una aplicación de consumidor escrita con ADO. La mayoría de los desarrolladores (especialmente los desarrolladores de Microsoft Visual Basic y C# de Microsoft) utilizan ADO o ADO.NET para aplicaciones de consumidor. El consumidor de prueba debe cubrir todas las áreas funcionales del proveedor. Para obtener un ejemplo de una aplicación de consumidor ADO, vea [ejemplos de código ADO en Microsoft Visual Basic](https://msdn.microsoft.com/library/ms807514.aspx).  
  
1. Ejecute las pruebas de conformidad de OLE DB (incluidas las pruebas de conformidad de ADO) para asegurarse de que el proveedor cumple el estándar de nivel 0 para proveedores OLE DB. (Para obtener una explicación del nivel 0, busque "OLE DB Level 0 Conformance Tests" en [Guía del programador de OLE DB](/previous-versions/windows/desktop/ms713643\(v=vs.85\)). Estas pruebas y la documentación asociada se incluyen con Visual C++ en el SDK de Data Access. Estas pruebas también ayudan a garantizar que el proveedor se ejecuta correctamente cuando se agrega otro [los proveedores de servicios](../../data/oledb/ole-db-resource-pooling-and-services.md) y son especialmente útiles si modifica o agregar propiedades. Para obtener más información acerca de las pruebas de conformidad, vea el archivo Léame para el SDK de Data Access, que se encuentra en uno de los CDs de Visual Studio.  
  
## <a name="see-also"></a>Vea también  

[Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)