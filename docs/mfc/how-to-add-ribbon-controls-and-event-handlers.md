---
title: "Cómo: agregar controles de la cinta y controladores de eventos | Documentos de Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-windows
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- event handlers [MFC], adding
- ribbon controls [MFC], adding
ms.assetid: b31f25bc-ede7-49c3-9e3c-dffe4e174a69
caps.latest.revision: "9"
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: f5d5015fdf5fd2a97b6b8a9b9ee9cf5ccc755ce5
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="how-to-add-ribbon-controls-and-event-handlers"></a>Cómo: Agregar controles de cinta y controladores de eventos
Los controles de cinta de opciones son elementos, como botones y cuadros combinados, que agregan a los paneles. Los paneles son las áreas de la barra de cinta que mostrarán un grupo de controles relacionados.  
  
 En este tema, abra el Diseñador de la cinta de opciones, agregará un botón y, a continuación, vincule un evento que muestra "Hello World".  
  
### <a name="to-open-the-ribbon-designer"></a>Para abrir el Diseñador de la cinta de opciones  
  
1.  En Visual Studio, en el **vista** menú, haga clic en **vista de recursos**.  
  
2.  En **vista de recursos**, haga doble clic en el recurso de cinta de opciones para mostrarla en la superficie de diseño.  
  
### <a name="to-add-a-button-and-an-event-handler"></a>Para agregar un botón y un controlador de eventos  
  
1.  Desde el **barra de herramientas**, haga clic en **botón** y arrástrela hasta un panel en la superficie de diseño.  
  
2.  Haga clic en el botón y haga clic en **Agregar controlador de eventos**.  
  
3.  En el **Asistente para controladores de eventos**, confirme la configuración predeterminada y haga clic en **agregar y editar**. Para obtener más información, consulte [Asistente para controladores de eventos](../ide/event-handler-wizard.md).  
  
4.  En el editor de código, agregue el código siguiente en la función de controlador:  
  
 ```  
    MessageBox((LPCTSTR)L"Hello World");

 ```  
  
## <a name="see-also"></a>Vea también  
 [Ejemplo RibbonGadgets: Aplicación de Gadgets de cinta de opciones](../visual-cpp-samples.md)   
 [Diseñador de la cinta de opciones (MFC)](../mfc/ribbon-designer-mfc.md)

