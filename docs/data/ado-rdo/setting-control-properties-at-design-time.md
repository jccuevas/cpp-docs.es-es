---
title: "Establecer las propiedades de un control en tiempo de dise&#241;o | Microsoft Docs"
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
  - "controles ActiveX [C++], propiedades"
ms.assetid: 963bf498-d371-4cfd-8bed-865427dcfad9
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Establecer las propiedades de un control en tiempo de dise&#241;o
[!INCLUDE[vs2017banner](../../assembler/inline/includes/vs2017banner.md)]

Las propiedades de los controles se pueden establecer en tiempo de diseño mediante el editor de cuadros de diálogo.  Cuando establezca el valor de una propiedad, el editor de recursos inicializará el control con el valor especificado.  Podrá modificar el valor de la propiedad mediante programación.  
  
 La propiedad **DataSource**, presente en todos los [controles enlazados a datos](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md) permite especificar el control de [código fuente](../../data/ado-rdo/databinding-with-activex-controls-in-visual-cpp.md) con el que desea establecer un enlace.  
  
 Al enlazar controles enlazados a datos de ADO mediante enlace simple a un control de datos ADO \(ADODC, *ADO Data Control*\), debe asociar el control a una columna estableciendo el valor de la propiedad **DataField** del control en un campo válido del conjunto de filas.  De no hacerlo así, la aplicación compilada produce una aserción en una compilación de depuración en ejecución \(la aserción consiste simplemente en marcar que se ha enlazado el control a una columna de valores NULL\).  
  
> [!NOTE]
>  La ficha de propiedades **General** permite especificar un identificador de control y otras propiedades necesarias para el archivo .rc. El archivo .rc se compila después para generar un código de recurso de programa de Windows.  
  
### Para establecer una propiedad en la ficha Todas  
  
1.  [Inserte un control ActiveX](../../data/ado-rdo/inserting-the-control-into-a-visual-cpp-application.md) en un cuadro de diálogo.  
  
2.  Haga clic con el botón secundario en el control en el editor de cuadros de diálogo y, a continuación, haga clic en **Propiedades**.  
  
3.  Haga clic en la ficha **Todas** para mostrar las propiedades del control.  Para una propiedad determinada, escriba el valor de inicialización.  
  
 Para establecer las propiedades de un control en tiempo de ejecución, vea [Modificar el comportamiento de un control en tiempo de ejecución](../../data/ado-rdo/modifying-a-control-s-run-time-behavior.md).  
  
## Vea también  
 [Utilizar controles ActiveX](../../data/ado-rdo/using-activex-controls.md)