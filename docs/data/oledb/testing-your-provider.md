---
title: Probar un proveedor | Documentos de Microsoft
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
ms.openlocfilehash: c35b1391e5b8cbfb073255b3680b0376d19ae040
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
ms.locfileid: "33104794"
---
# <a name="testing-your-provider"></a>Probar un proveedor
Antes de liberar un proveedor, deberá realizar las pruebas siguientes, en el orden indicado. Estas pruebas garantizan el proveedor funciona correctamente para la mayoría de los usuarios potencial.  
  
1.  Pruebe el proveedor mediante una [consumidor](../../data/oledb/creating-an-ole-db-consumer.md) aplicación escrita con las plantillas de consumidor OLE DB. El consumidor de prueba debe cubrir todas las áreas funcionales del proveedor (todo el código que se ha agregado o modificado).  
  
2.  Probar el proveedor mediante una aplicación de consumidor programada con ADO. Mayoría de los desarrolladores (sobre todo los desarrolladores de Microsoft Visual Basic y C# de Microsoft) usa ADO o ADO.NET para aplicaciones de consumidor. El consumidor de prueba debe cubrir todas las áreas funcionales del proveedor. Para obtener un ejemplo de una aplicación de consumidor ADO, vea [ejemplos de código ADO en Microsoft Visual Basic](https://msdn.microsoft.com/en-us/library/ms807514.aspx).  
  
3.  Ejecute las pruebas de conformidad de OLE DB (incluidas las pruebas de conformidad de ADO) para asegurarse de que el proveedor cumple el estándar de nivel 0 para proveedores OLE DB. (Para obtener una explicación del nivel 0, busque "OLE DB Level 0 Conformance Tests" en [Guía del programador de OLE DB](http://go.microsoft.com/fwlink/p/?linkid=121548). Estas pruebas y la documentación asociada se incluyen con Visual C++ en el SDK de Data Access. Estas pruebas también ayudan a garantizar que el proveedor se ejecuta correctamente cuando se agrega por otro [proveedores de servicios](../../data/oledb/ole-db-resource-pooling-and-services.md) y son especialmente útiles si modifica o agrega propiedades. Para obtener más información acerca de las pruebas de conformidad, vea el archivo Léame para el SDK de Data Access, que se encuentra en uno de los CDs de Visual Studio.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)