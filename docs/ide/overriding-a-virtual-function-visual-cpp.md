---
title: "Reemplazar una funci&#243;n virtual (Visual C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "article"
f1_keywords: 
  - "vc.codewiz.virtualfunc.override"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "clases base, reemplazar funciones virtuales definidas en"
  - "Propiedades (ventana), reemplazar funciones virtuales en"
  - "funciones virtuales, reemplazar"
ms.assetid: 2d8c76f2-7a6b-4c9c-8de5-4282ce7755b6
caps.latest.revision: 7
caps.handback.revision: 7
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Reemplazar una funci&#243;n virtual (Visual C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Se pueden reemplazar las funciones virtuales definidas en una clase base desde la [ventana Propiedades](../Topic/Properties%20Window.md) de Visual Studio.  
  
### Para reemplazar una función virtual en la ventanas Propiedades  
  
1.  En la Vista de clases, haga clic en la clase.  
  
2.  En la ventana Propiedades, haga clic en el botón **Invalidaciones**.  
  
    > [!NOTE]
    >  El botón **Invalidaciones** está disponible al seleccionar el nombre de la clase en la Vista de clases o al hacer clic dentro de la ventana de código fuente.  
  
     La columna izquierda enumera las funciones virtuales.  Si el nombre de una función virtual también aparece en la columna derecha, ello quiere decir que ya se ha implementado una función de reemplazo.  
  
3.  Si la función no posee ningún reemplazo, haga clic en la celda de la columna derecha en la ventana Propiedades para mostrar el nombre sugerido para la función de reemplazo como \<add\>*FuncName.*  
  
4.  Haga clic en el nombre sugerido para agregar código auxiliar a la función.  
  
5.  Para modificar una función de reemplazo, haga doble clic en el nombre de la función en la Vista de clases y modifique el código en la ventana de código.  
  
 Para quitar un reemplazo, haga clic en el nombre de la función de reemplazo en la columna derecha y seleccione \<delete\>*FuncName.* El código de la función queda convertido en comentarios.  
  
## Vea también  
 [Agregar funcionalidad con los Asistentes para código](../ide/adding-functionality-with-code-wizards-cpp.md)   
 [Agregar una clase](../ide/adding-a-class-visual-cpp.md)   
 [Agregar una función miembro](../ide/adding-a-member-function-visual-cpp.md)   
 [Agregar una variable miembro](../ide/adding-a-member-variable-visual-cpp.md)   
 [Controlador de mensajes de MFC](../mfc/reference/adding-an-mfc-message-handler.md)   
 [Explorar la estructura de clases](../ide/navigating-the-class-structure-visual-cpp.md)