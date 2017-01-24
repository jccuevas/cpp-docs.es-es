---
title: "Depurar un proveedor | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "depurar [C++], proveedores"
  - "proveedores OLE DB, depurar"
  - "depurador de Visual C++"
  - "depurador de Visual C++, depurar proveedores"
ms.assetid: 90d4e7db-06ea-4de0-a7f4-4f3751d50d93
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Depurar un proveedor
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Hay dos formas de depurar un proveedor:  
  
-   Como los proveedores se crean en proceso, puede crear código de consumidor mediante las plantillas de consumidor OLE DB y recorrer el código del proveedor de la forma normal.  
  
-   Puede utilizar la utilidad ITEST incluida en Visual C\+\+.  
  
### Para utilizar la utilidad ITEST  
  
1.  Abra el proyecto de proveedor.  
  
2.  En el menú **Proyecto**, haga clic en **Configuración**.  
  
3.  En el cuadro de diálogo **Páginas de propiedades**, haga clic en la ficha **Depurar**.  
  
4.  En el cuadro **Archivo ejecutable para la sesión de depuración**, seleccione la aplicación ITEST.  
  
5.  Establezca puntos de interrupción y, a continuación, depure de la manera habitual.  
  
## Vea también  
 [Trabajar con plantillas de proveedores OLE DB](../../data/oledb/working-with-ole-db-provider-templates.md)