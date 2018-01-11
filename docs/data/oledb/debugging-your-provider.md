---
title: Depurar un proveedor | Documentos de Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- debugging [C++], providers
- OLE DB providers, debugging
- Visual C++ debugger, debugging providers
- Visual C++ debugger
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
caps.latest.revision: "7"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
- data-storage
ms.openlocfilehash: 6cfcb90daaf23a5fd8e248d43b920340e38d8057
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
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