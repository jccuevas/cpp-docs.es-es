---
title: Depurar un proveedor | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-data
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: c6258ddd3fd4317c608cb20486c364918fb5c73a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 05/04/2018
---
# <a name="debugging-your-provider"></a>Depurar un proveedor
Hay dos maneras de depurar el proveedor:  
  
-   Dado que los proveedores se crean en proceso, puede crear algún código de consumidor mediante las plantillas de consumidor OLE DB y el paso en el proveedor normalmente.  
  
-   Puede utilizar la utilidad ITEST que se incluye con Visual C++.  
  
### <a name="to-use-the-itest-utility"></a>Para utilizar la utilidad ITEST  
  
1.  Abra el proyecto de proveedor.  
  
2.  En el **proyectos** menú, haga clic en **configuración**.  
  
3.  En el **páginas de propiedades** cuadro de diálogo, haga clic en el **depurar** ficha.  
  
4.  En el **archivo ejecutable para sesión de depuración** , seleccione la aplicación ITEST.  
  
5.  Establecer puntos de interrupción y, a continuación, depuración como de costumbre.  
  
## <a name="see-also"></a>Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)