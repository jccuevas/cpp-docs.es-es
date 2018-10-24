---
title: Depurar un proveedor | Microsoft Docs
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
ms.openlocfilehash: fc4461bb29bb9b9c706177c4dcd2134d37d697e0
ms.sourcegitcommit: c045c3a7e9f2c7e3e0de5b7f9513e41d8b6d19b2
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 10/24/2018
ms.locfileid: "49989910"
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