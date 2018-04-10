---
title: Agregar compatibilidad con ATL a un proyecto MFC | Documentos de Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-windows
ms.tgt_pltfrm: ''
ms.topic: article
f1_keywords:
- vc.codewiz.adding.atl.mfc
dev_langs:
- C++
helpviewer_keywords:
- MFC, ATL support
- ATL, MFC projects
ms.assetid: b5fe15d6-7752-4818-b9f9-62482ad35c95
caps.latest.revision: 10
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 92a4e9096cf72f6556c8ceb36e12cdff97139712
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: es-ES
ms.lasthandoff: 12/21/2017
---
# <a name="adding-atl-support-to-your-mfc-project"></a>Agregar compatibilidad con ATL a un proyecto MFC
Si ya ha creado una aplicación basada en MFC, puede agregar compatibilidad para Active Template Library (ATL) fácilmente mediante la ejecución de agregar compatibilidad de ATL para proyectos de MFC.  
  
> [!NOTE]
>  ATL y MFC no se admiten normalmente en las ediciones Express de Visual Studio.  
  
> [!NOTE]
>  Esta compatibilidad solo se aplica a objetos COM simples añadidos a un ejecutable MFC o un proyecto DLL. Puede agregar otros objetos COM (incluidos los controles ActiveX) a proyectos MFC, pero los objetos podrían no funcionar según lo esperado.  
  
### <a name="to-add-atl-support-to-your-mfc-project"></a>Para agregar compatibilidad con ATL a un proyecto MFC  
  
1.  En el Explorador de soluciones, haga clic en el proyecto al que desea agregar compatibilidad con ATL.  
  
2.  En el menú contextual, haga clic en **agregar**y, a continuación, haga clic en **Agregar clase**.  
  
3.  Seleccione el **agregar compatibilidad con ATL al proyecto MFC** icono.  
  
    > [!NOTE]
    >  Este icono se encuentra en la carpeta ATL, en el **categorías** panel.  
  
4.  Cuando se le solicite, haga clic en **Sí** para agregar compatibilidad con ATL.  
  
 Para obtener más información acerca de cómo agregar compatibilidad con ATL cambia el código del proyecto MFC, vea [detalles sobre la compatibilidad agregada por el Asistente para ATL](../../mfc/reference/details-of-atl-support-added-by-the-atl-wizard.md)  
  
## <a name="see-also"></a>Vea también  
 [Agregar una clase](../../ide/adding-a-class-visual-cpp.md)   
 [Agregar funcionalidad con los asistentes para código](../../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una función miembro](../../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una Variable miembro](../../ide/adding-a-member-variable-visual-cpp.md)   
 [Reemplazar una función Virtual](../../ide/overriding-a-virtual-function-visual-cpp.md)   
 [Controlador de mensajes MFC](../../mfc/reference/adding-an-mfc-message-handler.md)   
 [Navegar por la estructura de clases](../../ide/navigating-the-class-structure-visual-cpp.md)
